# Show dynamic inventory

[ec2-user@ip-172-31-47-39 ansible-aws-lab]$ ansible-inventory -i inventories/aws_ec2.yml --graph
@all:
  |--@ungrouped:
  |--@aws_ec2:
  |  |--Ansible
  |--@env_SIT:
  |  |--Ansible

 # Ping the listed host

## Start SSH agent and add your key
eval $(ssh-agent -s)
ssh-add ~/.ssh/ansible_key.pem

## Verify key is added
ssh-add -L

## Now it should work
ansible -i inventories/aws_ec2.yml Ansible -m ping

# Run playbook on particular host got from the dynamic host

ansible-playbook -i inventories/aws_ec2.yml copy-file.yml --limit "Ansible"

  
