---
title: "Can I login to a root desktop?"
date: 2008-12-13
forum: General Help
---

### Post by Heeter on 2008-12-13
Hi all,

Was wondering, is there someway that I can login to the root user desktop GUI?

I have a couple of issues that I would like to resolve in that environment.

Thanks

Heeter

---

### Post by blakjesus on 2008-12-13
Well, i think its against the forum policy to say how to do that, because it is against Ubuntu's model of security.

Although you can probably accomplish the same things by using a root terminal by using this command:

> sudo -s

and supplying a password.

---

### Post by bluefrog on 2008-12-13
give root a password and change the security in gdm.conf

but there's nothing more you will do as root in a GUI except breaking more things very likely

---

### Post by aysiu on 2008-12-13
Don't use *sudo -s*, as that will give you a root prompt using the user's environment, which can lead to problems.

If you're at the command prompt, use ```
sudo -i
``` instead.

If you would prefer a graphical environment to make root changes, create a keyboard shortcut or launcher for the command ```
gksudo nautilus
``` Here's a guide:
[Make a &#8220;browse as root&#8221; launcher in Ubuntu](http://www.psychocats.net/ubuntucat/rootlauncher/)

---

### Post by sisco311 on 2008-12-13
[New forum policy on log-in-as-root tutorials]("http://ubuntuforums.org/showthread.php?t=716201")

You can use sudo and gksu to run a program as root.
for example you can start a root shell:
```
sudo -i
```
run a single command as root:
```
sudo command
```

for gui applications use gksu:
```
gksu command
```
to start the file manager (nautilus) as root:
```
gksu nautilus
```

If you have a more specific question, please feel free to ask, we would be glad to respond.

---

### Post by blakjesus on 2008-12-13
Thanks for clarifying that, i had no clue.

I don't mean to hijack the thread but could you explain the difference between these sudo commands?

```
sudo -i
sudo -s
sudo su
```

I have at different points been told to use one of those.

---

### Post by Heeter on 2008-12-13
Thanks guys,

I need but five minutes in there, just fixing up a couple of minute user issues. 

Thanks again,

Heeter

---

### Post by morphos on 2008-12-13
> **Heeter said:**
> Thanks guys,

I need but five minutes in there, just fixing up a couple of minute user issues. 

Thanks again,

Heeter

Best of luck with Google.  Forum rules dictate that posting this solution is not permitted.

---

### Post by sisco311 on 2008-12-13
> **blakjesus said:**
> Thanks for clarifying that, i had no clue.

I don't mean to hijack the thread but could you explain the difference between these sudo commands?

```
sudo -i
sudo -s
sudo su
```

I have at different points been told to use one of those.

[https://help.ubuntu.com/community/EnvironmentVariables]("https://help.ubuntu.com/community/EnvironmentVariables")

```
sudo -i    #(equivalent to **sudo su -** , gives you roots environment configuration)
```

```
sudo -s    #(equivalent to **sudo su**, keeps the current shell's environmen)
```

example:
```
#sudo -i
#echo $HOME
**/root**
#exit
```

```
#sudo -s
#echo $HOME
**/home/yourusername**
#exit
```

---

