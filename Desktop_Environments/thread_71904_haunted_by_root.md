---
title: "haunted by root"
date: 2005-10-04
forum: Desktop Environments
---

### Post by geofff on 2005-10-04
When I originally loaded Ubuntu 12 months ago I didn't understand sudo and activated root with a separate root password.  Subsequently having discovered the error of my ways I disabled root: "sudo passwd -l root". 

I vaguely remember various fumbles before arriving at this point but nevertheless believed I had then resolved the situation. If only! 

By opening terminal (and root terminal) from my main account I can now carry out admin with sudo. However if the gui hangs and I try to do admin from console (cnrl alt 1-6) I am not allowed in. I insert my username and (sudo) password but am not recognised although these do work in terminal mode. I have tried my own username with all root/sudo passwords previously used (I think) but nothing works. I have done the same with "root". 

Despite having "disabled" root it appears to still apply in console mode and I now don't know what the password is. 

How can I get rid of root once and for all, not just disable it but get rid of it, so that hopefully console will let me in again?

---

### Post by mlomker on 2005-10-04
> How can I get rid of root once and for all, not just disable it but get rid of it, so that hopefully console will let me in again?

You can't get rid of root--most of the system files are owned by root.  I'm surprised that disabling it doesn't allow it to work from a terminal...all of how-to's suggest doing what you did.

The easiest thing would be to just re-enable the account and give it a password.

```

sudo passwd root -u
sudo passwd root

```

---

### Post by XDevHald on 2005-10-04
In order to reset your root accounts password, you can follow these steps provided in the wiki how to so that you may do so. **sudo passwd root -u** / **sudo passwd root** does NOT allow you to do so, if you're needing to reset because you don't have your password, this won't work because it will tag you to give it the password (in which you don't have)

[http://wiki.clug.org.za/index.php/How_do_I_reset_my_root_password%3F]("http://wiki.clug.org.za/index.php/How_do_I_reset_my_root_password%3F")

Please follow the correct steps, and note that you can't remove root or else you're just not wanting to do basically anything, you need root no matter what. Your account can not become root at ALL.

---

### Post by geofff on 2005-10-04
Thanks for the above. (sudo passwd root -u) It worked re root. I now have root working from both terminal and console. 

I therefore assumed the same would work if I substitued my username for root. It didn't! I can still sudo in terminal mode from the gui but cannot log in with my (sudo or any other) username from the console. It appears that terminal and console have two separate passwords for me! 

Does this make sense?

---

### Post by geofff on 2005-10-04
Steve
Thanks for your info. I assume this is why I cannot get my sudo-user account to work. I'll have a go at this tomorrow. 

Thanks both for the help.

Geofff

---

### Post by mlomker on 2005-10-04
> this won't work because it will tag you to give it the password (in which you don't have)

He stated in his post that sudo was working fine, hence my approach to the problem.

---

### Post by cwaldbieser on 2005-10-04
[QUOTE=geofff]Thanks for the above. (sudo passwd root -u) It worked re root. I now have root working from both terminal and console. 

I therefore assumed the same would work if I substitued my username for root. It didn't! I can still sudo in terminal mode from the gui but cannot log in with my (sudo or any other) username from the console. It appears that terminal and console have two separate passwords for me! 

Does this make sense?[/QUOTE]
Not really.  The passwords are all kept in the same place, no matter how you log in.  It is really odd that you can log in from the GUI login but not from the console.

If you create a new (normal) user can you log into the terminal as that user?  If not, the only thing I can think of is that somehow your terminal settings are messed up so the characters you type are not being correctly interpreted in the terminal.

---

### Post by geofff on 2005-10-05
[QUOTE=geofff]It appears that terminal and console have two separate passwords for me! [/QUOTE]
Oops. Machine is set up to automatically enable caps lock which automatically de-enables it in console mode! Didn't spot this! I can now login as main user with sudo password! 

However I still cannot do admin in console. For instance in both sudo and root mode in console when doing "gedit /etc/samba/smb.conf" I get an error message: 
"(gedit:7891):Gtk-WARNING**: cannot open display:" 

From gui terminal in sudo mode I can open it no problem and work with it.

From gui root terminal it opens a blank smb.conf file and the terminal has an error message: 
"(gedit:8116): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed."
(This is also the case if I do "sudo" in root terminal - just thought I might try!)

So console is still of little use to me although I can sudo shutdown!

TIA

Geofff

---

### Post by mcduck on 2005-10-05
[QUOTE=geofff]
However I still cannot do admin in console. For instance in both sudo and root mode in console when doing "gedit /etc/samba/smb.conf" I get an error message: 
"(gedit:7891):Gtk-WARNING**: cannot open display:" 
From gui terminal in sudo mode I can open it no problem and work with it.[/QUOTE]Well, gedit is GUI program and therefore not usable in console. If you want a simple, easy-to-use editor for console you could install jed. It's very similiar to edit in dos/windows, and way easier to learn than vi.

---

### Post by geofff on 2005-10-05
[QUOTE=mcduck]Well, gedit is GUI program and therefore not usable in console.[/QUOTE]
Thanks. I didn't know that! However what's causing the error message when using gedit from the gui root terminal?

Geofff

---

### Post by mlomker on 2005-10-05
> From gui root terminal it opens a blank smb.conf file and the terminal has an error message: 
"(gedit:8116): GnomeUI-WARNING **: While connecting to session manager:


That's a security feature.  :p 

You can do this:

```

xhost local:
sudo gedit

```

I actually added the following line to my ~/.bashrc file to make it permanent:

```

xhost local: > /dev/null 2>&1

```

---

### Post by geofff on 2005-10-06
[QUOTE=mlomker]
I actually added the following line to my ~/.bashrc file to make it permanent:
```

xhost local: > /dev/null 2>&1

```[/QUOTE]
Don't think I'll do that until I'm less of a threat to my system!

In fact knowing there arn't any gremlins lurking I feel safe to close root down again and just work with sudo. Thanks for bearing with me. If it wasn't for guys like you I wouldn't be with Ubuntu.

---

