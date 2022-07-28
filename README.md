# Ansible Script For Squid and HAProxy Setup

## Steps to Run Squid Automation Script 
<ol>
    <li> Update the list of servers in myhosts file under Squid group.</li>
    <li> Check the ansible.cfg and update the remote_user.</li>
    <li> Uncomment "private_key_file = /path/to/key " under defaults section of ansible.cfg file if required.</li>
    <li> Update variables in squid_vars.yml file as per requirement</li>
    <li> Add the Domain name in templates/domain_list.acl to block the site to access from Squid Proxy Server. </li>
    <li> Run - "ansible-playbook squid.yml" to start the script. Add --check in cmd for dry run. </li>
</ol>

### How to Update the Variables ( squid_vars.yml )
##### squid_port

The Port on which Squid should listen to. 
Default - 3128

##### permitted

This is the IP or a range of ip addresses from which squid will accept the connection calls.
Examples - 
1. 192.168.1.136/32 # Allowing a Single IP
2. 192.168.1.0/24 # Allowing a CIDR Range of IPs
3. 192.168.1.55-192.168.255.255 # Range of IPs

##### authenticate

Enable this function if required to authenticate the access to Squid Proxy.
Default - True

##### auth_username

Provide username which can access to squid proxy.

##### auth_password

Password for username which can access to squid proxy.

##### namespace

Namespace of K8s on which to create the Deployments
