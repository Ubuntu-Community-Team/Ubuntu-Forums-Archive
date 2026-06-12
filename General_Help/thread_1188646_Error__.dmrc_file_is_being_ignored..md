---
title: "Error : .dmrc file is being ignored."
date: 2009-06-15
forum: General Help
---

### Post by chandu73 on 2009-06-15
Hi,
am running ubuntu8.04 verison on my desktop.
it worked fine for me several days, suddenly one day when i started my desktop it's giving me an error stating $HOME /.dmrc file being ignored, this prevents default session .....

so i fixed that issue in following way

sudo chmod 644 .dmrc
sudo chown user_name .dmrc
sudo chmod 755 /home/user_name
sudo chown  /home/user_name

then i can login to my user account.
but the problem is when i started the sysytem next day, the same problem came.
pls help me how can i fix so that i shud not need to change the settings daily.

and one more problem is i need to set the environmenta varible PATH settings, in which file i need to change them, i can do it from CLI but the change is temporary, how to fix it permanently.

Regards
Chandu

---

### Post by unutbu on 2009-06-15
644 is the wrong permission for .dmrc I think. 
Perhaps try this guide to fix dmrc issues: [http://ubuntuforums.org/showthread.php?p=6208727](http://ubuntuforums.org/showthread.php?p=6208727)

Edit: Sorry -- on second thought, the instructions there look remarkable similar to what you've already tried...

---

### Post by unutbu on 2009-06-15
Feel free to ignore my previous post. It was obviously unencumbered by the thought process.

To set the PATH variable you can edit ~/.profile. Put 

```
PATH=$PATH:/whatever/path/you/like
export PATH
```

in ~/.profile. Then logout and log back in and the PATH will be set.

After you manually fix .dmrc, log out and log back in. What does 
```

ls -l ~/.dmrc 
```

say? It should look like this:
```

-rw------- 1 user_name user_name 28 2009-06-15 10:46 /home/user_name/.dmrc

```

---

### Post by drs305 on 2009-06-15
I wrote the guide referenced previously. It was probably a typo when you posted it, but the last command in your first post was missing the username.

Try:
```

sudo chown [COLOR="DarkRed"]username[/COLOR] /home/[COLOR="DarkRed"]username[/COLOR]/.dmrc
chmod 644 /home/[COLOR="DarkRed"]username[/COLOR]/.dmrc
sudo chown [COLOR="DarkRed"]username[/COLOR] /home/[COLOR="DarkRed"]username[/COLOR]
chmod 755 /home/[COLOR="DarkRed"]username[/COLOR]

```

The main reason I'm posting is to note you do not need *sudo* for the *chmod* command since you already own the files if you run them in the order posted above. It is generally a good habit *not* to use *sudo* unless you must.

Looks like *unbuntu* has your second question covered.

---

### Post by chandu73 on 2009-06-16
hi, 

thanks for quick reply, with the instructions u mentioned helped me to solve the prblm of .dmrc

still i have the prblm in Environment PATH, as u said i modified the ~/.profile but it's not working , i tested it by giving the command "echo $PATH , then am not getting the bin directory what i mentioned.
if i change the setting in ~/.bashrc that is effecting n showing me when i give command echo $PATH.
but when am compiling the uClinux distribution , it's giving not able to find the path.

how can i fix this issue

Regards
chandu

---

### Post by drs305 on 2009-06-16
> **chandu73 said:**
> still i have the prblm in Environment PATH, as u said i modified the ~/.profile but it's not working , i tested it by giving the command "echo $PATH , then am not getting the bin directory what i mentioned.
if i change the setting in ~/.bashrc that is effecting n showing me when i give command echo $PATH.
but when am compiling the uClinux distribution , it's giving not able to find the path.

Since you mention compiling, it is possible you need to change root's $PATH as well. Depending on how you are invoking admin privileges (sudo -i/sudo or sudo su), you will need to set the $PATH in /root/.bashrc or /etc/environment for root operations. You must refresh the $PATH for this to take effect by closing the terminal window or running "source .bashrc" once you have invoked a root shell.

---

### Post by nola504 on 2009-06-21
Seems like the .dmrc issue is related to granting too much permission to 'everyone' on your home folder.

In many cases setting your home folder to 755 will not fix the problem and is also pretty invasive being that you are mangling existing permissions such as which files are executable and what not.

The best way to solve this issue is to issue the following commands:
```
sudo chown -R username:username ~/
sudo chmod -R o= ~/
sudo chmod 644 ~/.dmrc
```

The first command is simply making sure you own all the files in your folder (don't forget to change 'username' to your actual username). You might receive the error 'Permission denied' for the .gvfs folder. This is fine you can ignore it.

The second command removes all permission for 'everyone'. This means that only you can access your files which is what that .dmrc error is really complaining about. This command is less invasive because you are preserving your existing permissions assigned to you. A good thing. However, if you've already been playing around with permissions on your home folder you may have to resort to the more drastic 750.

The third command makes sure you have write permission to your .dmrc file.

Hope this helps someone.

---

