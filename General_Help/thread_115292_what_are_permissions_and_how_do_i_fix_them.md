---
title: "what are permissions and how do i fix them?"
date: 2006-01-10
forum: General Help
---

### Post by RikkiD04 on 2006-01-10
i get this message before i log on:

"Your $HOME/.dmrc file has incorrect permissions and is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions."

could someone instruct me on how to fix that? i can't figure out how to open the terminal either

---

### Post by nkhansen on 2006-01-10
Permissions is a way of telling people what they can do to the files. Basic file permissions are READ, WRITE, and EXECUTE.

you can change permissions through nautilus in GNOME in the file properties dialog.

I actually think that the problem is that $HOME/.dmrc is owned by root instead of you. You can fix that by running

$ sudo chown <username>:<username> $HOME/.dmrc

If that does not do the trick, try

$ chmod 644 $HOME/.dmrc

chmod changes permissions, chown CHanges OWNer.

---

### Post by RikkiD04 on 2006-01-10
where would i type all that?

---

### Post by lamego on 2006-01-10
You need to switch to the terminal.
CTRL-ALT-F1
login with your user and password:
then type:
sudo chmod 644 $HOME/.dmrc

---

### Post by RikkiD04 on 2006-01-10
thanks, i did that and it said "sudo: must be a setuid root". so i added a colon in front of sudo, and nothing happened, so i logged out, but the screen is still up. did it do something? and how do i exit that screen?

---

### Post by jrib on 2006-01-10
[QUOTE=RikkiD04]thanks, i did that and it said "sudo: must be a setuid root". so i added a colon in front of sudo, and nothing happened, so i logged out, but the screen is still up. did it do something? and how do i exit that screen?[/QUOTE]

ALT-F7 will take you back to X

---

### Post by RikkiD04 on 2006-01-10
i'm still recieving the same message that my $HOME/.dmrc file has incorrect permissions. is there another way to change it? i've already tried the above codes

---

### Post by nkhansen on 2006-01-10
I must admit that I don't know why the message "must be a setuid root" comes up. When you wrote the stuff I told you to, did you write the "$"'s too? You are not supposed to do that. Here's how it is supposed to behave.

You write (supposed your username is rikki):

sudo chown rikki:rikki /home/rikki/.dmrc


The computer will prompt you for a password (which you type)

And that should be it. Do you still get the "must be a setuid root" message? Are you the system administrator? If not, then you have to get the system administrator (the one who installed ubuntu) to do the stuff for you.

---

### Post by RikkiD04 on 2006-01-10
i did that, and i've checked the permissions of that file, and they match what they are supposed to be, but i still get the message. it's starting to get a little frustrating since i've been working on it since 8:30 this morning. but hopefully my brother will be home soon and will be able to fix it for me. if you have any more ideas, though, please enlighten me!

---

### Post by nkhansen on 2006-01-10
It has the right permissions, but what about the owner? Do you own it, or is root the owner?

---

### Post by Corvillus on 2006-01-10
Yeah, no setuid root permissions on sudo is wierd...it looks like what you're probably going to have to do is boot into recovery mode. This *should* give you a root shell. If you get a root shell, what you should do is
```
apt-get --reinstall install sudo
```
to reinstall sudo. Then
```
chown -R username:username /home/username/
```
to set the user as the owner of the dir (replacing all instances of "username" with your username). Then reboot normally.

---

### Post by BLTicklemonster on 2006-09-05
Here's how I fixed my setuid problem:

I went into the recovery console (reboot, and chose recovery console in case you didn't catch on to how to do that), and typed 

ls -l usr/bin/sudo 

and the readout looked fine, like this 

```
-rwsr-xr-x 1 root root 93844 2006-05-17 08:41 /usr/bin/sudo
```

but I knew better...


so I put 

chwon root:root /usr/bin/sudo
then
chmod 4755 /usr/bin/sudo

then I typed 

reboot


and I now have sudo again.

---

