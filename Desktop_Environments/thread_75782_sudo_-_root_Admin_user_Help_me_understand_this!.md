---
title: "sudo - root? Admin user? Help me understand this!"
date: 2005-10-14
forum: Desktop Environments
---

### Post by elefthera on 2005-10-14
OK, I chdir to a directory owned by root - (/etc say); then try "sudo echo hello > bit.txt". That gets me "permission denied". But I thought the whole point of sudo is to give me superuser control...

If this sounds naive I'm used to using normal root user in other distros, so I'm still a bit unclear about a disto with no root (though I understand the reasons for it).

What's going on?

(PS have just upgraded and updated...)

---

### Post by valter on 2005-10-14
sudo echo tere > tere.txt
tried -  worked for me

---

### Post by Wolki on 2005-10-14
[QUOTE=elefthera]OK, I chdir to a directory owned by root - (/etc say); then try "sudo echo hello > bit.txt". That gets me "permission denied". But I thought the whole point of sudo is to give me superuser control...
[/QUOTE]

this should not happen. Is the directory set to read-only, perhaps?

If you're used to a root user and occasionally want the functionality, there is a small trick to become root without enabling a root user: "sudo su" will work :)

---

### Post by ssam on 2005-10-14
this is a wierd thing that bash does

according to [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Redirecting the output of commands run with sudo can catch new users out (consider "sudo ls > /root/somefile"). Workarounds for this include using "sudo sh -c 'ls > /root/somefile'" (but escaping for this gets very ugly very quickly), using [WWW] Adverbio, or simply using sudo -s to get a root shell and going from there

    *MattZimmerman: A simple approach which works for most cases is to use dd(1): ls | sudo dd of=/root/somefile

you can also do

```
sudo su
```
or
```
sudo bash
```

to get a root shell

---

### Post by ChrisTheGeek on 2005-10-14
Hi elefthera,

The command you typed seems like it should have worked - sudo does indeed give you super-user rights.  Have you added multiple users? If so, make sure your current user is allowed to use sudo.

If you're still stuck, you can enable the root account or just find out more about sudo here:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by drogoh on 2005-10-14
EDIT:  Note to self - don't post right when you wake up.

---

### Post by elefthera on 2005-10-14
[QUOTE=ChrisTheGeek]The command you typed seems like it should have worked [/QUOTE]

Yes, I'm certain that it should. but it doesn't. And it's not just redirecting - what originally brought the problem to light was a refusal to save the result of:

"sudo kate /etc/samba/smb.conf"

That should definitely work. The redirect thing was just to help fine-tune the problem.

FWIW I have done almost nothing (eg not even adding users) since installing from the install CD which I downloaded yesterday, so I can't see it's anything I've done. All relevant folders and files are rwxr-xr-x.

Most confusing... Any other ideas, anyone?

---

### Post by GeneralZod on 2005-10-14
[QUOTE=elefthera]Yes, I'm certain that it should. but it doesn't. And it's not just redirecting - what originally brought the problem to light was a refusal to save the result of:

"sudo kate /etc/samba/smb.conf"
[/QUOTE]

kate has bizarre issues with sudo; try kwrite instead.

---

### Post by ssam on 2005-10-14
do you think sudo not play nice with bash builtins could be considered a bug?

```
sudo cd /home
```

does not work

---

### Post by FlipFlop on 2005-10-14
[QUOTE=elefthera]OK, I chdir to a directory owned by root - (/etc say); then try "sudo echo hello > bit.txt". That gets me "permission denied". But I thought the whole point of sudo is to give me superuser control...
[/QUOTE]

So you didn't get asked for your password after entering the sudo command ?

That would suggest as previously mentioned that you are not a member of the admin group that grants the use of sudo.

So the permission denied meant not that the command failed but that you wasn't allowed to sudo.

---

### Post by elefthera on 2005-10-14
[QUOTE=GeneralZod]kate has bizarre issues with sudo; try kwrite instead.[/QUOTE]

Well, this is interesting...

jim@brian:~$ sudo kwrite /etc/samba/smb.conf
Password: [entered as normal]
Error: "/var/tmp/kdecache-jim" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Error: "/tmp/kde-jim" is owned by uid 1000 instead of uid 0.
Link points to "/tmp/kde-root"
Error: "/tmp/ksocket-jim" is owned by uid 1000 instead of uid 0.
Link points to "/tmp/ksocket-root"

...but despite the errors, the above worked (I changed and saved the file). Then, after closing kwrite:

jim@brian:~$ sudo kate /etc/samba/smb.conf
Error: "/var/tmp/kdecache-jim" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
kate: ERROR: Communication problem with kate, it probably crashed.

No sign of Kate starting up...!

Any chance those errors are caused by me trying out another poster's idea (sudo su)?

Does this help us?

---

### Post by GeneralZod on 2005-10-14
[QUOTE=elefthera]
Any chance those errors are caused by me trying out another poster's idea (sudo su)?

Does this help us?[/QUOTE]

To be quite honest, I have no idea what's going on ;)

Kubuntu, very sadly, always seems to have issues with sudo (some have reported that the inability to change to admin mode from within kcontrol, a major bug in 5.04, still affects 5.10 - although others claim that a completely fresh install shouls solve this).  I'd advise sticking with kwrite and hoping for an eventual fix :/

---

### Post by elefthera on 2005-10-14
> **GeneralZod]To be quite honest, I have no idea what's going on  said:**
> 

Ha! Such candour is delightful!

[QUOTE=GeneralZod]Kubuntu, very sadly, always seems to have issues ... admin mode from within kcontrol

Ah, well, put me down for that one too!

I'm now seriously wondering whether I should start again with the raw Gnome version; I'd prefer KDE (it's what I'm more familiar with), but above all I'd prefer something that works, and I'm not sure Kubuntu is there yet.

Thanks for your help anyway.

---

