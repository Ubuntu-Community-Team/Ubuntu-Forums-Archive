---
title: "how to change folder permissions"
date: 2007-05-15
forum: Desktop Effects &amp; Customization
---

### Post by jlkz on 2007-05-15
i'm in a terminal and i got to 
root@jk:~#

and i have no idea what to do to change the permissions so i can save things in to folders.

---

### Post by hartz on 2007-05-16
> **jlkz said:**
> i'm in a terminal and i got to 
root@jk:~#

and i have no idea what to do to change the permissions so i can save things in to folders.

**The Short Answer:**

to give your non-root user access to write to a folder run this command:

```
chmod a+rwx /path/to/folder
```

**Long answer:**

**[COLOR="Red"]Don't do it.[/COLOR]**  At least, don't do it for any system folders.  Don't do it for /etc, /var, /usr, /opt and any other system folders.  You have access to your home and that is the right place to keep your files.  It makes it easy to backup your personal data, and upgrades etc will leave it alone (unless you re-partition and wipe the disk)

If you install a new hard disk drive on your computer, you may want to use that to supplement you personal user disk space.  For example if you mount it as "/mydata" you can give access to either everybody, or to your own login ID, to write to this disk at this mountpoint.  The command would be:


```
chmod a+rwx /mydata
```

Note:  The "#" in your prompt above indicates that you have a root shell, and therefore access to hose your system and break things.  You should steer clear from using the root shell until you know how to avoid this sort of thing.

The better, safer way of doing this is to run all commands as a non-privileged user (You will have a $ prompt), and to then prepend the "sudo" command to any commands that HAVE to run with elevated privileges.

Example:
```
sudo chmod a+rwx /mydata
```

And as hinted previously you could give access to just one user by making that user the owner of the mounted file system, with this command:

```
sudo chown *john */mydata
```

If you want to know why the chown or chmod commands work, just say the word and I'll post a short-ish explanation.

---

### Post by kragh on 2007-05-20
I am trying to download a file to a folder with root permissions only. Root is not going to be enabled. Is there a way to do this without changing the permissions on the folder? Appreciate any help.

---

### Post by hartz on 2007-05-21
The chmod command below would enable you to save as file into that folder from your web browser or other download program.  After saving the file, you should change the permissions back.

However you really just shouldn't be doing that.  Rather download the file into your home directory, desktop, or any other convenient temporary location.  Then copy the file into the root-owned directory ...

If I may ask, why do you want to do this?  What downloaded file would you want to put into a root-owned directory?

---

### Post by kragh on 2007-05-21
When I try to save a download i.e.Postfix source to etc/local/src it needs root access. If I dnload to a user and then try to copy it still needs root permissions on some folders.

---

### Post by hartz on 2007-05-22
OK ..... If you're planning on building/compiling software, I would recommend the following:

1. Download the tarbal to your Desktop or any such convenient location.
2. open a Terminal
3. In the terminal assume root permissions with this command:
```
sudo -s
```
Your prompt will change from a "$" to a "#" after you enter the password.
4. extract the tarbal into the source location, eg /usr/local/src, with a command similar to this
```
cd /usr/local/src
tar xzvf /home/[COLOR="Red"]username[/COLOR]/Desktop/[COLOR="Magenta"]package-1.2.3-4.tar.gz[/COLOR]

```
in the above "[COLOR="Red"]username[/COLOR]" is the login ID you use, and [COLOR="Magenta"]package-1.2.3-4.tar.gz[/COLOR] is the file you downloaded.
5. This will create some new directory, it should be clear from the lines scrolling by where the new files have been extracted to.  Change into this directory, with a command similar to
```
cd package-1.2.3-4
```
6. read the README file, with a command similar to this
```
less README*
```
7. Follow the build instructions.

Question:  What's wrong with the pre-build postfix in the apt databases (synaptic) ?

---

### Post by Elimist on 2007-05-24
Could anyone tell me the command that effects all subfolders?
There's a folder I'm trying to delete, and I changed the permissions to my username, but when I try and empty the recycle bin it says "cannot remove [whatever]".

Or perhaps there's a sudo command that allows me to remove a folder and all of it's contents, ignoring subfolders and files?

---

### Post by hartz on 2007-05-24
To remove files that you do not own, recursively, in a directory called "[COLOR="Red"]dirname[/COLOR]":

```
sudo rm -r [COLOR="Red"]dirname[/COLOR]
```

To Take ownership of a direcotry and all of its contents, recursively:
```

sudo chown -R [COLOR="Blue"]newuser [/COLOR][COLOR="Red"]dirname[/COLOR]
```

For this, specify your own login name where I indicated [COLOR="Blue"]newuser[/COLOR].

WARNING:

Recursively deleting or chown-ing files are extremely dangerous.  You wil not be the first, nor the last, person to add one too many spaces into the command.  This example will hose your system:

```
sudo rm -r / home/john/Desktop/tempfiles
```

Note the space between the first / and home.

You have been warned.

---

### Post by Elimist on 2007-05-25
Is a typo the only risk?
I just want to make sure.

---

### Post by hartz on 2007-05-25
Of course not.

You might think that doing
```
rm -r /
```
is safe, and then issue the command correctly (no typo), and still end up hosing your system.

---

### Post by kragh on 2007-05-28
I have three books on Postfix and one of them "Linux Email" by Rolf Hilderbrandt among others suggests the option of compiling from source code or installing from a package. I finally ended up installing using synaptic and everything is well bu I have now to update the version. The instructions are clear but the source code dd not compile for various reasons. I think one of the reasons relates to permissions. I am still looking for the definitive answer to the question of whether using an update client for a dynamic IP is compatible with postfix. I have yet to go on tjhe public nic but am able to send email inside the lan.

---

