---
title: "What does 'run as root' mean, how's it done?"
date: 2009-01-10
forum: General Help
---

### Post by frankwakeman on 2009-01-10
I've been having trouble getting advice about some of the more arcane Linux methods.  I have a driver for Vodafone Mobile broadband with a .run suffix.  I naively just double-clicked it first but was told 'run as root'.  How do I do his?

To make it idiot proof, say the file is on my desktop and is called voda.run, can you tell me what I do?  Thanks.  I don't think I set up a root account, by the way.

Thanks.

---

### Post by Hangwire on 2009-01-10
Use

```
sudo
```

to do things as root. It will ask you for your password.

---

### Post by jgoguen on 2009-01-10
With Ubuntu, "run as root" means to use **sudo**.  To run this file as root:

[LIST]
[*]Open a terminal (Applications -> Accessories -> Terminal)
[*]Type **cd ~/Desktop** and press Enter
[*]Make sure it's executable: type **chmod +x voda.run** and press Enter
[*]Type **sudo ./voda.run** and press Enter
[*]Enter your password (the one you logged in with) and press Enter
[/LIST]

That's it, voda.run is now running as root.  You're right, you didn't set up a root account.  Ubuntu disables root by default, leaving you to do everything through sudo.  Check out [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for more information.

---

### Post by DeMus on 2009-01-10
> **frankwakeman said:**
> I've been having trouble getting advice about some of the more arcane Linux methods.  I have a driver for Vodafone Mobile broadband with a .run suffix.  I naively just double-clicked it first but was told 'run as root'.  How do I do his?

To make it idiot proof, say the file is on my desktop and is called voda.run, can you tell me what I do?  Thanks.  I don't think I set up a root account, by the way.

Thanks.

Your first account, the one you created during installing Ubuntu, is automatically assigned privileges to run as root.

Open a terminal: Applications | Accessories | Terminal
Type:
cd /Desktop

In the terminal it now says: username@pcname:~/Desktop

Now type:
ls -l

You get a list of everything which is on your Desktop

Type:
chmod +x filename
ls -l

Now your file should have x's in the status columns.

Type:
sudo ./filename
Enter your password

Your file should run now.

If it does not you can try:
sudo sh ./filename

If this also doesn't work then I also don't know how to start it. But I am pretty sure it will work this way. Good luck.

DeMus

---

### Post by Vorian Grey on 2009-01-10
Root is where you have super user powers and can do anything up to deleting your entire system. You use that power by typing sudo in the terminal. It's not to be used lightly.

---

### Post by steveneddy on 2009-01-10
> **jgoguen said:**
> With Ubuntu, "run as root" means to use **sudo**.  To run this file as root:

[LIST]
[*]Open a terminal (Applications -> Accessories -> Terminal)
[*]Type **cd ~/Desktop** and press Enter
[*]Make sure it's executable: type **chmod +x voda.run** and press Enter
[*]Type **sudo ./voda.run** and press Enter
[*]Enter your password (the one you logged in with) and press Enter
[/LIST]

That's it, voda.run is now running as root.  You're right, you didn't set up a root account.  Ubuntu disables root by default, leaving you to do everything through sudo.  Check out [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for more information.

+1

very good explanation

---

### Post by HunterK on 2009-01-10
A typical user would need "sudo" mostly for installing new applications via apt-get or synaptic. Also, when you get that "Software update" message and it asks you to login, you are effectively "running as root" when you do that.

---

### Post by kaibob on 2009-01-10
The following community document gives a lot of useful information on root, sudo, and the like:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ithanium on 2009-01-10
Use sudo bofore your commands. This will run your commands as root.

---

