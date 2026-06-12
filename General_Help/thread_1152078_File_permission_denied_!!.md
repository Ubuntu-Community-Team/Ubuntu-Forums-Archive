---
title: "File permission denied !!"
date: 2009-05-07
forum: General Help
---

### Post by Dragon6 on 2009-05-07
Hi , I'm kind of beginner to linux world
I'm having 8.10 and trying to manipulate with nsswitch.conf
user@user-laptop:~$ /etc/nsswitch.conf
bash: /etc/nsswitch.conf: Permission denied
I tried to give it some permissions like :
chmod u+x /etc/nsswitch.conf
and then chmod g+x /etc/nsswitch.conf
and then chmod u+w /etc/nsswitch.conf
and then chmod u+x /etc/nsswitch.conf
I know what "u" and "g" means but tried though 
the problem is when i type " /etc/nsswitch.conf " in terminal , the same output comes out which is : bash: /etc/nsswitch.conf: Permission denied
why is that ? should I be able to access this file if I change those permissions ?
Thanks

---

### Post by chango77745 on 2009-05-07
You may want to use the code brackets for you code when you are writing in a forum.

Have you tried typing in 
```
sudo
```

before the rest of your code to give yourself admin privledges.

For example:
```
sudo gedit /etc/nsswitch.conf
```

---

### Post by Dragon6 on 2009-05-07
I already tried to become as a super user using sudo
but if I try to to use gedit command , then what would the purpose of the permissions be :D ?
Thanks for your response

---

### Post by baseface on 2009-05-07
only root should be able to edit system-wide config files. dont change the permissions on them. only change permissions on things that YOUR user owns.

---

### Post by Dragon6 on 2009-05-07
my own user , you mean the files in /home partition ?

---

### Post by Dngrsone on 2009-05-07
sudo only applies to the command following it.

So, by prepending sudo to your gedit command, it should open up the text editor as root, allowing you to edit the file and save it afterward.

---

### Post by Dragon6 on 2009-05-07
again , if I use gedit command , then what's the purpose of the permissions i gave

---

### Post by Dngrsone on 2009-05-07
> **Dragon6 said:**
> again , if I use gedit command , then what's the purpose of the permissions i gave

None.  But the thing is-- it looks like you are trying to invoke a configuration file.  If you want to **change** the configuration, you do so **by editing** the configuration file.  You can do so by **using gedit**, which happens to be a text editor.

---

### Post by Yellow Pasque on 2009-05-07
Use gksudo for GUI programs:
```
gksudo gedit /etc/nsswitch.conf
```

---

### Post by Dragon6 on 2009-05-07
so i understand that if i apply those permissions to another file ( not a configuration file or text file ) would that take effect ?

---

### Post by Dngrsone on 2009-05-07
> **Temüjin said:**
> Use gksudo for GUI programs:
```
gksudo gedit /etc/nsswitch.conf
```

Thanks, Temüjin, [this is why](http://psychocats.net/ubuntu/graphicalsudo).

We learn new things every day!

---

### Post by Dngrsone on 2009-05-07
> **Dragon6 said:**
> so i understand that if i apply those permissions to another file ( not a configuration file or text file ) would that take effect ?

Yes.  There are times when you will have to make a file executable after downloading and such but changing permissions for the sake of doing so can lead to disastrous results.

---

### Post by Dragon6 on 2009-05-07
Thanks for responses and help ...

---

### Post by bodhi.zazen on 2009-05-07
Permissions are perplexing to new users. See if this helps :

[FilePermissions - Community Ubuntu Documentation]("https://help.ubuntu.com/community/FilePermissions") 

When you run an editor as root , say

gksu gedit 
sudo -e
sudo nano
sudo vim

you are NOT changing the permissions of the file you are editing, you are running the editor as root. Since root owns the file, root can edit the file.

Same as if you run

gksu nautilus

---

