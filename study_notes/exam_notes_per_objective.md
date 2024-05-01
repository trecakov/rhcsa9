## Exam Objectives EX200V9K - with notes 

### Understand and use essential tools 
- Access a shell prompt and issue commands with correct syntax 
- Use input-output redirection (>, >>, |, 2>, etc.)
	- '>' - redirect to a file
   	- '>>' - append to a file
	'2>' - redirect stderr to a file
	'2>>' - redirect stderr to a file and append
	'2>&1' redirect stderr to stdout
	'/dev/null' - data sent to /dev/null is lost
	
- Use grep and regular expressions to analyze text 
	'grep --help' - help on how to use the tool and its flags/options
	'grep patern filename'
	'-i' - case insensitive
	'-v' - not containing the pattern
	
	examples:
	'grep "^ssl" file.txt' - search for lines in file.txt that are starting with 'ssl'
	'grep "ssl$" file.txt' - search for lines in file.txt that are ending with 'ssl'
	'grep "[s|S]sl" file.txt' - search for lines in file.txt that are starting with lower or upper letter 's' and match the pattern 'ssl'
	'grep "^[abc]" file.txt' - search for characters in file.txt that are not contained in brackets
	'grep "^$" file.txt' - search for empty lines in file.txt
	'grep -v "^#" file.txt' - search for uncommented lines in file.txt
	
- Access remote systems using SSH 
	'ssh-keygen' - generate a ssh key
	'ssh-copy-id username@hostname' - copy ssh key to hostname server under .ssh directory of username
	'ssh username@hostname' - connect via ssh protocol
	'scp username@hostame:/path/to/file.txt /location/on/local/machine' - secure copy from remote machine to a local server
	'scp /location/on/local/machine/file.txt username@hostame:/location/on/remote/machine' - secure copy from local machine to a remote server
	'sftp username@hostname' - sftp protocol, type '?' after connection for help
	
	For help on how to use these tools and their flags, type:
	'ssh-keygen --help' 
	'ssh-copy-id --help'
	'ssh --help'
	'scp --help' 
	'sftp --help'
	
- Log in and switch users in multi-user targets
	'su user' - log in to an interactive shell(.bashrs)
	'su - user' - log in to a login shell(.bash_profile)
	
- Archive, compress, unpack, and uncompress files using tar, star, gzip, and bzip2 
	'tar --help'
	
	examples:
	'tar -cf helloworld.tar hello world' - archive hello and world files/directories to helloworld.tar
	'tar -tvf helloworld.tar' - list files in helloworld.tar
	'tar -xf helloworld.tar' - extract files in helloworld.tar archive
	'tar -czvf helloworld.tar.gz hello world' - archive and compress hello and world files/directories to helloworld.tar.gz
	'tar -zxvf helloworld.tar.gz' - uncompress and unarchive helloworld.tar.gz
	'tar -cjvf helloworld.tar.bz2 hello world' - archive and compress hello and world files/directories to helloworld.tar.bz2
	
	'star --help'
	
	examples:
	'star -c -f=archive.tar file1 file2' - archive file1 and file 2 into archive.tar
	'star -x -f=archive.tar' - unarchive
	'star -cv -bz -f=/arhive.star.bz2 /usr/docs' - archive and compress uzing bzip2
	
	'gzip --help'
	
	examples:
	'gzip archive.tar' - compress to archive.tar.gz
	'gzip -d file.tar.gz' - uncompress to archive.tar
	
	'bzip --help'
	
	examples:
	'bzip archive.star' - compress to archive.tar.gz
	
	You will probably need to install star and bzip2 packages:
	'dnf install star bzip2'

- Create and edit text files 
	'touch file.txt' - create a text file
	'vi file.txt' or 'vim file.txt' - open a file.txt via vi or vim editors

	Some vi/vim commands:

	i — Switch to Insert mode.
	Esc — Switch to Command mode.
	:w — Save and continue editing.
	:wq or ZZ — Save and quit/exit vi.
	:q! — Quit vi and do not save changes.
	yy — Yank (copy) a line of text.
	p — Paste a line of yanked text below the current line.
	o — Open a new line under the current line.
	O — Open a new line above the current line.
	A — Append to the end of the line.	
	a — Append after the cursor’s current position.
	I — Insert text at the beginning of the current line.
	b — Go to the beginning of the word.
	e — Go to the end of the word.
	x — Delete a single character.
	dd — Delete an entire line.
	Xdd — Delete X number of lines.
	Xyy — Yank X number of lines.
	G — Go to the last line in a file.
	XG — Go to line X in a file.
	gg — Go to the first line in a file.
	:num — Display the current line’s line number.
	h — Move left one character.
	j — Move down one line.
	k — Move up one line.
	l — Move right one character.

	For more info visit: https://www.redhat.com/sysadmin/introduction-vi-editor

- Create, delete, copy, and move files and directories 
	'mkdir -p /mnt/testdir' - create a directory called testdir in /mnt directory
	'mkdir -p /mnt/testdir{1,2,3,4} - create a directories called testdir1, testdir2, testdir3, testdir4 in /mnt directory
	'touch test.txt testmove.txt' - create two text files called test.txt and testmove.txt
	'cp -r /mnt/testdir /tmp' - copy a directory testdir to /tmp
	'cp test.txt /mnt/testdir' - copy a test.txt file to /mnt/testdir
	'mv testmove.txt /mnt/testdir' - move testmove.txt to /mnt/testdir

- Create hard and soft links 
	HardLink - same inode number; on;y for files and not directories
	'ln sourcefile linkfile' 
	SoftLink - different inode number; both for files and directories
	'ln -s source link'
	
	To verify:
	'ls -li source/link'

- List, set, and change standard ugo/rwx permissions 
	'ls --help' 
	'ls -lah' - will display all files and directories with their permissions, one per line in the present working directory
	
	'chmod --help' 
	'chown --help'
	
				symbol	octal 
	read		r		4
	write		w   	2
	executre	x  	 	1
	
	user(u)		group(g)	other(o)
	rwx 		rwx			rwx
	
	For more info visit: https://www.redhat.com/sysadmin/manage-permissions
	

- Locate, read, and use system documentation including man, info, and files in /usr/share/doc 
	'man httpd' - man pages on httpd
	'info httpd' - get info pages on httpd
	'man 8 httpd.socket' - get man page 8 on httpd.socket
	'whatis httpd' - more info about httpd
	'apropos httpd' - more info about httpd

### Create simple shell scripts 
- Conditionally execute code (use of: if, test, [], etc.) 
- Use Looping constructs (for, etc.) to process file, command line input 
- Process script inputs ($1, $2, etc.) 
- Processing output of shell commands within a script 

Here are few examples that cover these objectives:
```
#!/bin/bash
# Script to add users from an input file with user names listed 1 per line
# The first argument is input file

# Username file as input
USERFILE=$1

if [ "$USERFILE" = "" ]
then
        echo "Please specify an input file!"
        exit 10
elif test -e $USERFILE
then
        for user in `cat $USERFILE`
        do
			echo "Creating the "$user" user..."
            useradd -m $user

        done
        exit 20
else
        echo "Invalid input file specified!"
        exit 30
fi
```

You are given a userlist.txt that contains list of users, uid, and groups that they belong to.
```
### userlist.txt
manny:1010:dba_admin,dba_managers,dba_staff
moe:1011:dba_admin,dba_staff
```
```
#!/bin/bash
### Script to read userlist.txt and add users with respective uids and groups. 

while IFS=":" read -r user uid group
do useradd -u $uid -G $group $user;
done < userlist.txt
```

# For loop to add users from the file.
```
for user in 'cat userfile.txt'; do useradd -m $user; done
```

# For loop to add users from the list.
```
for user in joe jeff jennifer; do user add -m $user; done
```

# Find all files in /usr/share that are less than 1M in size and copy them to /root/myfiles directory.
```
find /usr/share -type f -size -1M -exec cp{} /root/myfiles \;
```


### Operate running systems
- Boot, reboot, and shut down a system normally 
	'reboot' - reboot
	'poweroff' - shut down
	'shutdown -h now' - shut down
	
- Boot systems into different targets manually 
	From maintanance mode add line 'systemd.unit=multi-user.target' and press ctrl+x to resume boot process.
	or
	from terminal type 'systemctl set-default multi-user'
	
	'systemctl list-units --type=target' - lists all targets on the system
	'systemctl get-default' - lists the current default target

- Interrupt the boot process in order to gain access to a system 
	1. When you reboot the server and grub2 boot screen comes up, press 'e'
	2. Go to the end of the line that starts with 'linux' and add 'rd.break'
	3. Press Ctrl+x
	4. 'mount -o rw,remount /sysroot'
	5. chroot /sysroot
	6. 'passwd root'
	7. 'touch /.autorelabel'
	8. 'exit'
	9. 'exit'
	
	These steps work for most RHEL versions besides 9.0. So if you are trying to do this on RHEL 9.0 there are 2 solutions.
	1. When you reboot the server and grub2 boot screen comes up, move with down arrow to the rescue kernel and press 'e'. Then follow the rest of above steps.
	2. Second solutions:
		1. When you reboot the server and grub2 boot screen comes up, press 'e'
		2. Go to the end of the line that starts with 'linux' and add 'init=/bin/bash', also change ro -> rw on the same line.
		3. Press Ctrl+x
		4. 'passwd root'
		5. 'touch /.autorelabel'
		6. '/usr/sbin/reboot -f'

- Identify CPU/memory intensive processes and kill processes 
	Use 'top' tool to view CPU/memory intensive processes and kill processes 
	'M' - to sort by Memory usage
	'P' - to sort by CPU/memory
	'U' - to sort by user
	'K' - to kill the process
	'R' - to renice the process
	
- Adjust process scheduling 
	'chrt --help' - this will give you enough info on how change priority/policy
	
- Manage tuning profiles 
	'dnf install tuned -y' - install tuned packages
	'systemctl enable --now tuned' - enable and start systemd tuned service
	'tuned-adm --help'
	'tuned-adm active' - list an active profile
	'tuned-adm profile' - lists all profiles
	'tuned-adm recommend' - lists recommended profile
	'tuned-adm profile virtual-guest' - changes active profile to virtual-guest
	'tuned-adm profile virtual-guest powersave' - changes active profile to multiprofile virtual-guest and powersave
	
	To configure dynamic tuning profile:
	1. change a dynamic_tuning value to 1 in /etc/tuned/tuned-main.conf
	2. restart the tuned service
	
- Locate and interpret system log files and journals 
	'journalctl --help'
	'journalctl -u chronyd' - lists anything related to unit chronyd 
	'journalctl -g systemd' - greps journals for systemd
	
- Preserve system journals 
	1. create a directory /var/log/journal
	2. modify storage variable in /etc/systemd/journald.conf to auto
	3. 'journalctl --flush'
	
- Start, stop, and check the status of network services 
	'systemctl --help'
	'systemctl start/stop/restart/status NetworkManager'
	
- Securely transfer files between systems 
	'scp username@hostame:/path/to/file.txt /location/on/local/machine' - secure copy from remote machine to a local server
	'scp /location/on/local/machine/file.txt username@hostame:/location/on/remote/machine' - secure copy from local machine to a remote server
	'sftp username@hostname' - sftp protocol, type '?' after connection for help
	'scp --help' 
	'sftp --help'

### Configure local storage 
- List, create, and delete partitions on GPT/MBR disks 
	fdisk(MBR) - used to create a master boot record-based partitions. Only 4 MBR partitions are able to be created on the system.
	gdisk(GPT) - used to create GPT partitions. Unlimited number of GPT partitons on the system.
	
	'fdisk -l' - lists all disks with a lot of info
	'lsblk -f' - info about disks, uuids, mountpoints, and fstypes.
	
	Creating gdisk/fdisk partition:
	'gdisk/fdisk /dev/sdb'
	'?' - for help
	'n' - new partition
	't' - change partition type
	'L' - list partition hex
	'p' - print to double check
	'w' - write
	
	Once partition has been created, we need to create filesystem(xfs,ext4,vfat), directory and mount it. If this mount needs to be persistent, add it to fstab.
	'mkfs.ext4 /dev/sdb1'
	'mkdir /web_project'
	'mount /dev/sdb1 /web_project'
	'echo "/dev/sdb1 /web_project ext4 defaults 0 0" >> /etc/fstab'
	
- Create and remove physical volumes 
	'pvcreate /dev/sd*' - create a physical volume
	'pvremove /dev/sd*' - remove a physical volume
	
- Assign physical volumes to volume groups 
	'vgcreate db_storage /dev/sd*'
	'vgremove -f db_storage'
	
- Create and delete logical volumes 
	'lvcreate -L 2G -n database db_storage' - creating a 2G in size logical volume named database, assigning db_storage volume group.
	'lvremove /dev/mapper/db_storate-database' - removing logical volume
	
- Configure systems to mount file systems at boot by universally unique ID (UUID) or label 
	Add something like this to /etc/fstab:
	'UUID=fe7d3d5a-7616-4f4e-9156-dbce80ec058d       /mnt/test   xfs     defaults        0       0'
	
- Add new partitions and logical volumes, and swap to a system non-destructively 
	Extending swap by creating a fdisk partition:
	'fdisk /dev/sdb'
	 1. 'n' - new partition
	 2. Enter for defaults
	 3. 't' - change partition type
	 4. 'L' - list partition hex
	 5. '82' - for swap type
	 6. 'w' - to write
	 
	 7. 'mkswap -L more_swap /dev/sdb1' - make swap with label 'more_swap'
	 8. 'swapon /dev/sdb1' - mount swap
	 9. 'swapon' - to check if new swap partition show as mounted
	 10. 'LABEL="more_swap"  none   swap     defaults        0       0' - add this line to /etc/fstab
	 
### Create and configure file systems 
- Create, mount, unmount, and use vfat, ext4, and xfs file systems 
	'mkfs.ext4 /dev/sdc1' - create ext4 on /dev/sdc1
	'mkfs.vfat /dev/sdc2' - create vfat on /dev/sdc2
	'mkfs.xfs /dev/sdc3' - create xfs on /dev/sdc3
	
	To resize fs:
	'xfs.grows /dev/mapper/vg_name-lv_name' - for xfs
	'resize2fs /dev/mapper/vg_name-lv_name' - for ext4 and vfat
	
- Mount and unmount network file systems using NFS 
	'dnf install nfs-* rpc-bind -y' - install nfs-* and rpc-bind packages
	'mkdir /exports/web_data{1,2}' - create directories to be exported
	'vi /etc/exports'
	/exports/web_data1 127.0.0.1(rw,sync,no_root_squash)
	/exports/web_data2 127.0.0.1(rw,sync,no_root_squash)
	
	'systemctl enable --now nfs-server' - enable and start nfs-server
	'showmounts -e' - show export mounts
	'firewalld --add-service=nfs,rpc-bind,mountd --permanent' - add/open services to the firewalld
	'firewalld --add-port=2049/tcp --permanent' - open port 2049 
	'mkdir /mnt/nfs_web_data{1,2}' - create mount directories
	'echo "127.0.0.1:/exports/web_data1 /mnt/nfs_web_data1 nfs defaults,_netdev 0 0" >> /etc/fstab' - adding mount point to fstab
	'echo "127.0.0.1:/exports/web_data2 /mnt/nfs_web_data2 nfs defaults,_netdev 0 0" >> /etc/fstab' - adding mount point to fstab
	'mount -a' - mount all
	
- Configure autofs 
	'dnf install nfs-* rpc-bind autofs-y' - install nfs-*, rpc-bind and autofs packages
	'vi /etc/auto.master' and add '/export/home /etc/auto.home' before the last line.
	'echo "* 127.0.0.1:/home/&" >> /etc/auto.home'
	'systemctl enable --now autofs rpc-bind'

- Extend existing logical volumes 
	'pvresize /dev/sdd' - if pv needs to be grown
	'lvextend --resize -L+3G /dev/mapper/db_storate-database' - grows the lv by 3G and resizes the filesystem

- Create and configure set-GID directories for collaboration
	'groupadd marketing_team' - create group
	'for i in manny mo jack; do useradd -m -G marketing_team $1;done' - for look to add users and assign them a group
	'mkdir /home/marketing_dir' - create shared directory
	'chown root:marketing_team /home/marketing_dir' - set ownership to root:marketing_team
	'chmod 770 /home/marketing_dir' - set rwx permisssions for user and group
	'chmod g+s,+t /home/marketing_dir' - set GID and sticky bit(no one can delete files that are not owned by them)
	
- Diagnose and correct file permission problems 

### Deploy, configure, and maintain systems
- Schedule tasks using at and cron 
	at - one time job
	cron - reocurring job
	
	'dnf install at cronie -y' - install at and cronie packages
	'systemctl enable --now atd crond' - enable and start atd and crond services
	'at 20:00' - schedule at job at 20:00
	 at> 'command' - command to run
	 at> 'ctrl+d' - ctrl+d to exit
	
	'at now +7 days'
	 at> 'command'
	 at> 'ctrl+d' 
	 
	'vi /etc/crontab' - you can see cronjob syntax and here you should add your job if it should run as root
	'crontab -l user' - lists cronjobs by that user
	'crontab -e user' - edit existing or add new cronjob
	
- Start and stop services and configure services to start automatically at boot 
	'systemctl start/stop httpd' - start/stop httpd service
	'systemctl enable --now httpd' - enable and start httpd
	'systemctl disable --now httpd' - disable and stop httpd
	
- Configure systems to boot into a specific target automatically 
	'systemctl list-units --type=target' - lists all targets on the system
	'systemctl get-default' - lists the current default target
	'systemctl set-default multi-user' - set default multi-user target
	
- Configure time service clients 
	'dnf install chrony -y' - install chrony package
	'vi /etc/chrony.conf' and change the with pool/iburst to where you want to point it.
	'server 169.254.169.254 iburst' - for example
	'systemctl enable --now chronyd' - enable and start chronyd service
	
	'chronyc sources -v' - list sources
	'chronyc makestep' - sync the time

- Install and update software packages from Red Hat Content Delivery Network, a remote repository, or from the local file system 
	'vi /etc/yum.repos.d/local.repo' - create a new repo file and add below lines with valid info.
	[local]
	name=local packages
	baseurl=https://
	enabled=1
	gpgcheck=0
	
	'dnf clean all' - clean all cache
	'dnf repolist --all' - list all repositories

- Modify the system bootloader 
	'vi /etc/default/grub' - file to modify the system bootloader
	'grub2-mkconfig -o /boot/grub2/grub.cfg

### Manage basic networking 
- Configure IPv4 and IPv6 addresses 
	'nmcli con show' - show connecitons
	'nmcli con mod ens192 ipv4.method "manual" ipv4 "192.168.10.240/24" ipv4.dns "192.168.10.145,8.8.8.8" ipv4.dns-search "testhostname.com" ipv4.gateway "192.168.10.1" ipv4.may-fail "no"
	'nmcli con mod ens192 ipv6.method "manual" ipv6 "2002:c0a8:a01:0:0:0:0:0164" ipv6.may-fail "yes"
	'nmcli con down ens192' - bring connection ens192 down
	'nmcli con up ens192' - bring connection ens192 up
	
	'nmtui' - gui tool to setup network configuration
	
- Configure hostname resolution 
	'hostnamectl set-hostname testhostname.com'
	
- Configure network services to start automatically at boot 
	'systemct enable --now NetworkManager'
	
- Restrict network access using firewall-cmd/firewalld
	'firewall-cmd --add-service=mysql --permanent' - permanently add mysql service
	'firewall-cmd --add-port=85/tcp --permanent' - permanently add port 85/tcp
	'firewall-cmd --remove-port=85/tcp --permanent' - permanently remove port 85/tcp
	'firewall-cmd --reload' - reload
	'firewall-cmd --list-all' - lists active rules
	'firewall-cmd --help' 
	
### Manage users and groups 
- Create, delete, and modify local user accounts 
	'useradd/usermod/userdel'
	'groupadd/groupmod/groupdel'
	
- Change passwords and adjust password aging for local user accounts 
	'passwd user' - change password for user
	'chage -L user' shows password policy(expiration)
	'chage user' - allows you to change password policy for that user
	
	To change defaults for all users:
	passwd length - /etc/security/pwquality.conf
	passwd expiration - /etc/login.defs
	
- Create, delete, and modify local groups and group memberships 
	'usermod -G group_name user' - add user to a new group
	'usermod -g group_name user' - change primary group for user
	'gpasswd -d user group' - remove user from a group

- Configure privileged  access 
	'visudo /etc/sudoers' 
	Uncomment some aliases and add lines at the bottom. For example:
	'%dba_admin ALL=SOFTWARE,SERVICES,PROCESSES' - dba_admin group should be able to run software, services, and processes
	'%dba_managers ALL=(ALL) ALL' - dba_managers group should have priveledges to run everything
	'%dba_intern ALL=MESSAGES' - dba_intern group should be able to check MESSAGES    

### Manage security 
- Configure firewall settings using firewall-cmd/firewalld 
	already covered
	
- Manage default file permissions 
	UMASK - default value is 666
	666 - 002(mask) = 664
	'echo 'umask 0027' >> ~/.bashrc' - will give a default permissions of 640
	
	ACL - access control lists
	'getfacl /home/docs' - show current acls on this directory/file
	'setfacl --help'
	
	For more info about ACLs visit: https://www.redhat.com/sysadmin/linux-access-control-lists

- Configure key-based authentication for SSH 
	already covered
	
- Set enforcing and permissive modes for SELinux 
	'getenforce' - check selinux current mode
	'setenforce 0/1' - 0=permissive
					 - 1=enforcing
					 
	for persistent setting, modify /etc/selinux/config.
	
- List and identify SELinux file and process context 
	'ls -Z'
	'ps aux Z'
	
- Restore default file contexts 
	'restorecon -Rv /web'
	
- Manage SELinux port labels 
	'semanage port -l | grep http' - list all port labels for http
	'semanage port -a -t http_port_t -p tcp 82' - set http_port_t label to port 82
	
- Use boolean settings to modify system SELinux settings
	'getsebool -a | grep httpd_can_sendmail' - will print if this label is on/off
	'setsebool -p httpd_can_sendmail on' - set this sebool label to on persistent

- Diagnose and address routine SELinux policy violations 
	'dnf install policycoreutils* setrouble*' - install help tools
	'journalctl -u httpd' 
	'grep httpd /var/log/messages | less'
	'grep httpd /var/log/audit/audit.log | less'

### Manage containers 
- Find and retrieve container images from a remote registry 
- Inspect container images 
- Perform container management using commands such as podman and skopeo 
- Build a container from a Containerfile 
- Perform basic container management such as running, starting, stopping, and listing running containers 
- Run a service inside a container 
- Configure a container to start automatically as a systemd service 
- Attach persistent storage to a container

	'podman --help'
	'podman login registry.access.redhat.com' - login to the registry
	'podman search registry.access.redhat.com/ubi9' - search container images
	'podman pull registry.access.redhat.com/ubi9/ubi:latest' - pull latest ubi container image
	'podman inspect docker://registry.access.redhat.com/ubi9/ubi:latest | less' - inspect 
	'podman run -it registry.access.redhat.com/ubi9/ubi:latest /bin/bash' - run a container(get a bash)
	'podman ps --all' - list running containers
	'podman rm <containerID>' - remove container
	'podman rmi <url>' - remove container image
	'podman build -t <tag_name> <url/containerfile>' - build a container from url or containerfile with a tag name
	'podman run -d <tag_name>' - run a container in the background
	'podman start <containerID>' - start container
	'podman stop <containerID>' - stop container
	'podman run -d -p 8000:8080 <url>' - run a container in the background, on local port 8000 and cointainer port 8080
	'podman run -d -n web_count -p 8000:8080 -v ~/web_data:/var/www/html:Z <url>' - run a container in the background, on local port 8000 and cointainer port 8080 with persistent storage mounted to ~/web_data and container name web_count
	
	For running a container as a systemd service, look at practive example.
	

Objectives taken from https://training-lms.redhat.com/public_content/redhat/training/Red%20Hat%20Certification%20Exam%20Objectives%20by%20Version.pdf
