# awx-operator-ansible
Ansible playbook to build awx-operator on Rocky Linux 8.

---
## Environment

* Rocky Linux 8.6 compatible 
* AlmaLinux 8.6, 8.7 compatible
* docker
* minikube
* awx-operator: 1.1.3

* aws: t3.xlarge + disk 50GB
* ibmcloud: bx2-4x16

---
## Require Ansible Collections
* community.general

---
## Usage

### 1.　clone repository

```
$ git clone git@github.com:yasu0519/awx-operator-ansible.git
```

### 2.　inventory setup

```
$ vi awx-operator-ansible/inventories/hosts
```

```
[awx]
xxx.xxx.xxx.xxx ansible_user=root ansible_ssh_private_key_file="/path/to/private_key"
```

* xxx.xxx.xxx.xxx: Specify the IP address or host name of the host you want to install.
* /path/to/private_key: Specify the file path of the private key of the host to install.

### 3.　run playbook

```
$ cd awx-operator-ansible
$ ansible-playbook awx.yml
```

---

## awx admin initial password for awx

* To retrieve the admin password, run

```
$ minikube kubectl -- get secret awx-demo-admin-password -n awx -o jsonpath="{.data.password}" | base64 --decode
```

