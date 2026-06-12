---
title: "password protect directories?"
date: 2005-11-03
forum: Desktop Environments
---

### Post by bionnaki on 2005-11-03
is there anyway to password protect directories? I'd like to have a few personal directories that require root password to read. Of course, I could change their ownership to root and change back & forward in a commandline, but this would be a hassle. is there any way to do this quickly in gui?

thanks

---

### Post by RAOF on 2005-11-03
Why would you want them to require a root password to read?  Wouldn't **your** password be a better idea?

I belive that if you set the permissions on the directory to "700" (chmod 700 <directoryname>), only your user will be able to access them.  Is this not enough?

---

### Post by bionnaki on 2005-11-03
no. I'd prefer a root password, so that some of my roomates couldnt read my personal files - chmod 700 will leave all those open to read when I am logged in as my primary user account (which would be *always* - even when I am away).

---

### Post by cbkm on 2005-11-03
[QUOTE=bionnaki]no. I'd prefer a root password, so that some of my roomates couldnt read my personal files - chmod 700 will leave all those open to read when I am logged in as my primary user account (which would be *always* - even when I am away).[/QUOTE]

So just do:
```

$ sudo chown -R root.root /path/to/my/private/directory

```
(in addition to the chmod given above)

Edit: meh, just read up and seen that you said you can do this to start with... ignore me ;)

Edit2: Could you not gksudo nautilis when you want to view the directories from the GUI?

---

### Post by doclivingston on 2005-11-03
You could change the owner to root, as well as modifying the permissions. The following will make it so that you have to use sudo/gksudo to access the directory.

```
chown root directory
chmod 700 directory
```

---

### Post by jrib on 2005-11-03
here is an easy way that I use:

1. make a folder using sudo: $sudo mkdir secretstuff (so yeah this gives ownership to root)
2. $sudo chmod 700 secretstuff (only root can read it)

And to view it you would just do "$sudo gedit secretstuff/secretfile" etc..  After you're done, you can kill the sudo session with $sudo -k.  

This might be similar to some of the stuff above, sorry if it is.  

And I guess this is a problem if on your box you have several sudoers but it it seems like your friends are just using your computer with your account.  If they had their own accounts then permissions alone would do it.

---

### Post by anniebrion on 2005-11-03
Can you not store your important files in a non-compressed password protected ZIP?

---

### Post by mgor on 2005-11-03
...and then just create a script for nautilus so you can right click the directory to open it with root permissions

~/.gnome2/nautilus-scripts/dir-root:
```
foo=`gksudo -u root -k -m "enter your password for root access" /bin/echo "Do you have root access?"`
sudo nautilus $NAUTILUS_SCRIPT_SELECTED_URIS
```

don't forget to `chmod +x` it.

([http://ubuntuforums.org/showthread.php?t=75610](http://ubuntuforums.org/showthread.php?t=75610))

---

### Post by bionnaki on 2005-11-03
[QUOTE=mgor]...and then just create a script for nautilus so you can right click the directory to open it with root permissions

~/.gnome2/nautilus-scripts/dir-root:
```
foo=`gksudo -u root -k -m "enter your password for root access" /bin/echo "Do you have root access?"`
sudo nautilus $NAUTILUS_SCRIPT_SELECTED_URIS
```

don't forget to `chmod +x` it.

([http://ubuntuforums.org/showthread.php?t=75610](http://ubuntuforums.org/showthread.php?t=75610))[/QUOTE]

thanks!
the password prompt was exactly what I was looking for.

---

### Post by HJThis on 2005-11-06
Hey,All

@mgor

When you say & don't forget to `chmod +x` it.

what are you saying 

Thank you

---

### Post by AndersAA on 2005-11-06
he's saying run chmod +x <scriptname> to enable the execute bit (allows executing it).

personally I'd just look into xscreensaver + locking, much simpler ;)

---

### Post by bdwalton on 2005-11-06
chmod +x will set the executable bit on the script mentioned above.  This allows it to be run as a program.  Otherwise, to run it you would have to do something like: sh <somescript without +x>

-Ben

---

### Post by HJThis on 2005-11-06
Hi,Both of you

Now i did the part about making the folder but this here no idea
do i do this in a Terminal talking about this 

Here

and then just create a script for nautilus so you can right click the directory to open it with root permissions

~/.gnome2/nautilus-scripts/dir-root:



Code:

foo=`gksudo -u root -k -m "enter your password for root access" /bin/echo "Do you have root access?"` sudo nautilus $NAUTILUS_SCRIPT_SELECTED_URIS

by the way can you tell i'm a newbie

Thank you

---

### Post by HJThis on 2005-11-06
Hmm

After looking at my post i don't get that script mentioned
at all.

Thank you

---

### Post by Black.Solaris on 2005-11-06
I am thouroughly confused!

Can some one go over this again step-by-step?  I know it is a lot to ask, but I am a newbie and this is confusing... I have only been using Ubuntu for about a week or two, and this is my first experience with Linux.

Thanks!

---

### Post by SickTwist on 2005-11-07
[QUOTE=bionnaki]no. I'd prefer a root password, so that some of my roomates couldnt read my personal files - chmod 700 will leave all those open to read when I am logged in as my primary user account (which would be *always* - even when I am away).[/QUOTE]

Why not configure xscreensaver to lock the screen when it activates? That way you can remain logged in all the time without the risk of users having access to  your files. If you wish to allow other users to use your machine, just create a guest account that does not have access to your home directory.

---

### Post by HJThis on 2005-11-07
Hey,All

Ok i get it after runing head in to wall all night
i now have a folder that needs you to input password
before you can open it.

Thank you

---

### Post by mgor on 2005-11-07
[QUOTE=HJThis]Hey,All

@mgor

When you say & don't forget to `chmod +x` it.

what are you saying 

Thank you[/QUOTE]

you have to make it executable, you chould right click the file in nautilus and set the executionsbits in the permissiontab aswell.

---

### Post by HJThis on 2005-11-07
Hi,mgor

Yes some how i got it working just great just what i was
looking for but thanks for the heads-up on this.

Best of luck

---

