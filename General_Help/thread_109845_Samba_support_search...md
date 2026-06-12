---
title: "Samba support search.."
date: 2005-12-29
forum: General Help
---

### Post by Lvnielen on 2005-12-29
situation:

-install Samba 
-edit the file smb.conf

[PHP]
[global]
	workgroup=FS
	net bios name = linuxleon
	time server = yes
	socket options = SO_KEEPALIVE IPTOS_LOWDELAY TCP_NODELAY
	wins support = no
	veto files = 
	security = user
	encrypt passwords = yes
	smb passwd file = /etc/samba/smbuser

[leon]
	path = /home/leon
	comment = map van leon
	available = yes
	browseable = yes
	public = yes
	writable = no
[/PHP]

- add a user
[PHP]sudo useradd pietjepuk[/PHP]
-give user a UNIX password
[PHP]sudo passwd pietjepuk[/PHP]
-give user a SMB password
[PHP]sudo smbpasswd -a pietjepuk[/PHP]

- i go to a windows server 2003 i do: 
 Start -> Run -> (type) \\linuxleon (or) the ip of mij samba server and press OK

i see the the windows logon for a shared folder whit als title ' connect to localhost.localdomain' then see i Connecting to linuxleon i can type my usrname and password en press ok(my username: pietjepuk and password) i press on OK and see the error: ' logon unsuccessfull: windows is unable to log you on. be sure that your user name and password are correct.' and i wish that my password and username are 100% correct....

who can tell me wat i do false?
who can me tell how to config step by step samba en its works by windows?

---

### Post by KnottyMan on 2005-12-29
I had to add 

server signing = auto
client signing = auto

to my global smb.conf for 2k3 to play nice.

---

### Post by Lvnielen on 2005-12-29
[PHP][global]
	workgroup=FS
	net bios name = linuxleon
	time server = yes
	socket options = SO_KEEPALIVE IPTOS_LOWDELAY TCP_NODELAY
	wins support = no
	veto files = 
	security = user
	encrypt passwords = yes
	smb passwd file = /etc/samba/smbuser
	server signing = auto
	client signing = auto[/PHP]

that works not

---

### Post by Lvnielen on 2005-12-29
no body?

---

### Post by rcerreto on 2005-12-29
I found useful enabling the samba user:

sudo smbpasswd -e pietjepuk

and then restarting the samba server

---

### Post by Lvnielen on 2005-12-30
[PHP]leon@linuxleon:~$ sudo smbpasswd -e pietjepuk
Failed to find entry for user pietjepuk.
Failed to modify password entry for user pietjepuk
[/PHP]

---

### Post by rcerreto on 2005-12-30
I assumed you created a "pietjepuk" user using

```
sudo smbpasswd -a pietjepuk
```

as posted earlier.

The steps are:
1) create a samba user
     sudo smbpasswd -a <username>

2) enable it
     sudo smbpasswd -e <same-username-used-before>

3) restart samba

Let me know whether it works or if you still have problems

---

### Post by Lvnielen on 2005-12-30
tanks it works!!

i have the next question?

Can i run Samba whitout all the usernames and passwords

i go to a windows machine en i do \\<ipadres> that i imidently see the shared folder and not logon and i see the shared folder?

---

