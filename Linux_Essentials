## some keywords to know

### ports: connection point

### Physical ports:

USB, Ethernet, HDMI, Displayport which are used to connect various devices

### virtual ports:

0-65535 port number. each is associated with specific services or protocols. data are transfered with it

21-FTP, 22-SSH, 23-Telnet,  25-SMTP,  53-DNS,  80-HTTP,  443-HTTPs,  3306-MySQL,  3389-RDP,  5432-PostgreSQL

### Vulnerability:

security weakness that are exploited by hackers

### CVE(Common Vulnerabilities and Explosures):

public directory that identifies known security vuln and exposures

### CVSS(Common Vulnerability scoring System):

used to measure the severity of vuln

### Exploit:

code or techique that enable the malicious use of vuln

### Zero Day:

vuln that are not yet patched and unknown to public and developers

### shell:

command line interface to use the service of a system. gaining it allow hacker to execute command on terget

### bind shell:

A type of shell where the attacker opens a port on the target machine and connects to it to execute commands.

### reverse shell:

A type of shell where the target machine connects back to the attacker's machine (attacker listening port), allowing the execution of commands.

### web shell:

A type of shell that includes a malicious script running on a web server, giving the attacker remote command execution capabilities.

### IPv4:

32-bit addressing system and provides approximately 4.3 billion unique addresses.

### IPv6:

Developed due to the insufficient addressing capacity of IPv4, it uses a 128-bit addressing system.

# Linux essentials:

## finding files

```jsx
//finding by name under directory
find / -name "notes.txt"

//Search by Type: Use the -type option to search by file type (regular files f, directories d)
find /home/user -type d -name "Project*"

//finding by file size
find / -size +50M

//Search by Modification Time: Use -mtime, -atime, or -ctime
find / -mtime -7

//Searching with the locate and which Command
updatedb
locate notes.txt
which python
```

## filtering

```jsx
head -n 3 /var/log/apache2/access.log
tail -n 3 /var/log/auth.log

$ cat names.txt
Bob
Alice
Charlie
Alice

$ sort names.txt
Alice
Alice
Bob
Charlie

$ sort names.txt | uniq
Alice
Bob
Charlie

//grep and wc
grep '192.168.1.1' /var/log/apache2/access.log
wc /etc/passwd
-l: Displays only the number of lines.
-w: Displays only the number of words.
-c: Displays only the number of bytes.
-m: Displays only the number of characters (useful for multi-byte character sets).

//awk command i know
```

## package management

package managers to facilitate tasks such as software installation, updating, and removal, dependency resolution, update, upgrade, configuration

```jsx
//searching in package list
sudo apt search htop
//to search a package starting with htop
sudo apt search ^htop
//search for package whose name contains htop
sudo apt search --names-only htop
//installing, upgrading, updating, remove i know
//The remove command does not delete the configuration files and deb files for htop. To remove those as well, you would use the purge command.
sudo apt purge htop
```

## user management

create, manage, and delete users in Linux

In Linux systems, users are defined as individuals or entities performing various tasks by logging into the system. User management is crucial for controlled access, resource allocation, and overall system administration.

a user is associated with a user account that has several attributes defining their identity and privileges within the system. These attributes include the username, UID (User ID), GID (Group ID), home directory, default shell, and password.

### Types of User

Linux supports two types of users: system users and regular users.

**System users** are created by the system during installation and are used to run system services and applications.

**Regular users** are created by an administrator and can access the system and resources based on their permissions.

```jsx
//creating a user 
//-u (uid), -d (directory), -s (default shell)
useradd -u 1002 -d /home/john -s /bin/bash john

//check or verify the user
$ id john
uid=1002(john) gid=1002(john) groups=1002(john)
//(gid = group id)

//registered users are stored in the /etc/passwd file
$cat /etc/passwd
root:x:0:0:System Administrator:/root:/bin/bash
john:x:1002:1002:John Doe:/home/johndoe:/bin/bash
// x = password. it is stored in /etc/shadow. so that filed is replaced by x

//changing user password
sudo passwd john

//remove a user named John and their associated files
sudo userdel john
```

## Group management

Groups are used to collectively assign the same access rights and permissions to multiple users. This enables system administrators to easily control resources and access

```jsx
//creating a group
sudo groupadd development

//see group info
$ cat /etc/group
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:
tty:x:5:
disk:x:6:
...
development:x:1004:

$ cat /etc/group | grep development
development:x:1004:

//adding a user in a group
sudo usermod -aG development john

//deleting a group
sudo groupdel development
```

## Permissions

when different users share the same system, privacy issues can easily arise. For instance, one user may not want others to view, edit, or delete their files.

```jsx
//see permission
$ ls -l
drwxr--r-- 2 john development 4096 Jul  29 12:34 notes.txt
// -d (represent directory), rwxr--r-- (file permission)
```

- user - User permissions concern only the owner of the file or directory.
- group - Group permissions concern only the users who belong to the group assigned to the file or directory.
- others - Other permissions concern all other users and groups on the system.

```jsx
rwx         r--     r--
user         group    others
// Members of the development group, to which the file is assigned, have only read permission for this file.

//using chmod for changing permissions
// u (user) - Owner user permissions
// g (group) - Group permissions
// o (others) - Other permissions
chmod o+w notes.txt
//giving others write permission

$ ls -l
drwxr--rw- 2 john development 4096 Jul  29 12:34 notes.txt

//giving all permission to both user, group and others
$ chmod ugo+rwx notes.txt
$ ls -l
drwxrwxrwx 2 john development 4096 Jul  29 12:34 notes.txt
```

## Process Management

process" is defined as a program loaded into memory and executing in the processor (CPU)

### Types of processes

Foreground process: 

By default, all processes run in the foreground. They take input from the keyboard and display output on the screen. Running the pwd command is a good example of a foreground process.

Background process: 

To run a command in the background, append the & character to it. For example, let's run the pwd command in the background

```jsx
pwd &
[1]   +   Done                 pwd
```

pwd command, by nature, completes its task immediately and exits. However, some commands run continuously until you send a stop signal. The ping command is a good example of this.

Let's send a ping to

127.0.0.1 with the ping command and run it in the background. This will allow us to send ping requests to 127.0.0.1 for as long as our terminal or the running process remains open, while still allowing us to use our terminal for other tasks.

```jsx
$ ping 127.0.0.1 &
[1] 54017
//[1] indicated the job number 1

$
64 bytes from 127.0.0.1: icmp_seq=100 ttl=64 time=0.081 ms
64 bytes from 127.0.0.1: icmp_seq=101 ttl=64 time=0.164 ms
64 bytes from 127.0.0.1: icmp_seq=102 ttl=64 time=0.075 ms

//To see the running jobs in the background, use jobs command
$ jobs
[1]    running    ping 127.0.0.1
```

To bring this background command back to the foreground, we can use the fg (foreground) command. We type the job number of the process with a % sign next to the fg command.

```jsx
$ fg %1
[1]  - running    ping 127.0.0.1
64 bytes from 127.0.0.1: icmp_seq=645 ttl=64 time=1.448 ms
64 bytes from 127.0.0.1: icmp_seq=646 ttl=64 time=0.161 ms
64 bytes from 127.0.0.1: icmp_seq=647 ttl=64 time=0.219 ms
64 bytes from 127.0.0.1: icmp_seq=648 ttl=64 time=0.130 ms
```

### managing system-wide process

processes used by the operating system, the terminal, service providers, or programs that continuously run in the background.

```jsx
//view system-wide process
$ ps

PID       TTY      TIME        CMD
19        pts/1    00:00:00    sh
24        pts/1    00:00:00    ps
```

| **Column Name** | **Description** |
| --- | --- |
| UID | User ID - The ID number of the user running the process |
| PID | Process ID - The unique identifier for the process |
| PPID | Parent Process ID - The unique identifier for the parent process that started the process |
| C | CPU - The CPU usage of the process |
| STIME | Start Time - The start time of the process |
| TTY | Terminal Type - The type of terminal where the process is running |
| TIME | The total time the process has been running |
| CMD | Command - The command that started the process |

```jsx
//kill a process
kill <pid>
kill 19

// if not work, forcefully stop it with -9
kill -9 19
```

## Network Management

## Network interface configuration

Ifconfig tool is used to perform various network configuration tasks such as assigning IP addresses, setting netmasks, and activating or deactivating network interfaces.

```jsx
//list available network devices
$ ifconfig

eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 172.20.1.109  netmask 255.255.255.0  broadcast 172.20.1.255
        inet6 fe80::5054:ff:fe10:72c3  prefixlen 64  scopeid 0x20<link>
        ether 52:54:00:10:72:c3  txqueuelen 1000  (Ethernet)
        RX packets 4542  bytes 352144 (343.8 KiB)
        RX errors 2  dropped 0  overruns 0  frame 2
        TX packets 1475  bytes 6213607 (5.9 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 11  memory 0xfc840000-fc860000  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 16  bytes 1888 (1.8 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 16  bytes 1888 (1.8 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

eth0: This is the Ethernet card interface. The UP flag indicates it is active. The IP address is 172.20.1.109. The MAC address is 52:54:00:10:72:c3.

lo: Loopback interface. It is a virtual interface created to allow local networking, pointing to the 127.0.0.1 IP address.

```jsx
//view specific network interface
ifconfig eth0

//view interfaces that are DOWN (i.e., inactive), use the -a parameter.
ifconfig -a

//activating and deactivation specific interface eth0
ifconfig eth0 up
ifconfig eth0 down

//assigning ip address to an interface or change the existing ip
ifconfig eth0 172.20.1.110

//assigning a netmask
ifconfig eth0 netmask 255.255.255.0 
```

### Promiscuous mode:

হলো একটি বিশেষ সেটিংস যা একটি **ইথারনেট কার্ড** বা নেটওয়ার্ক ইন্টারফেস কন্ট্রোলার (NIC)-কে তার স্বাভাবিক কার্যকারিতার বাইরে কাজ করতে দেয়।

- **স্বাভাবিক অবস্থায়:** একটি ইথারনেট কার্ড সাধারণত শুধুমাত্র সেই ডেটা প্যাকেটগুলোই গ্রহণ ও প্রক্রিয়া করে যেগুলোর **গন্তব্যের ম্যাক অ্যাড্রেস** (MAC Address) তার নিজের সাথে মিলে যায়, অথবা যেগুলো **ব্রডকাস্ট** (নেটওয়ার্কের সবার জন্য) করা হয়েছে। অন্য ডিভাইসের জন্য পাঠানো প্যাকেটগুলো এটি উপেক্ষা করে।
- **প্রমিস্কিউয়াস মোডে:** যখন এই মোড চালু করা হয়, তখন কার্ডটি **নেটওয়ার্ক ক্যাবলের** মধ্য দিয়ে আসা **সমস্ত** ডেটা প্যাকেট গ্রহণ করতে শুরু করে, সেগুলোর গন্তব্য অ্যাড্রেস যা-ই হোক না কেন—এমনকি সেগুলো যদি **অন্য কোনো ডিভাইসের** জন্য পাঠানো হয়ে থাকে। used for packet monitoring from various devices

```jsx
//enabling promiscuous mode
ifconfig eth0 promisc

//disabling promiscuous mode
ifconfig eth0 -promisc
```

### changing mac address

```jsx
ifconfig eth0 hw ether AA:BB:CC:DD:EE:FF
```

### DNS settings

In Linux, DNS settings are located in the /etc/resolv.conf file. 

```jsx
//editing resolve.conf
$ nano /etc/resolv.conf
nameserver 172.20.1.1

//file content is like
nameserver 172.20.1.1

//adding new dns server
//adding cloudflare dns, just add the dns server address
nameserver 1.1.1.1
nameserver 1.0.0.1
```

### SSH (Secure Shell)

a protocol used to securely connect to another computer over a network and execute commands.

```jsx
//installing ssh service
sudo apt-get update
sudo apt-get install openssh-server

//starting the service
sudo systemctl start ssh

//starting automaticallt every time of boots
sudo systemctl enable ssh

//connecting with a remote server with ssh
ssh user@ip_address
ssh root@192.168.1.100
```

### creating SSH key pair

you can connect without a password (and more securely) by using an SSH key pair. 

```jsx
//creating ssh key
ssh-keygen

//you have to copy the generated public key to the remote server
ssh-copy-id root@192.168.1.110
```

### SSH config file

location: /etc/ssh/sshd_config

```jsx
sudo nano /etc/ssh/sshd_config

//can edit port setting
port 2222

//after changing restart ssh service
sudo systemctl restart ssh

```
