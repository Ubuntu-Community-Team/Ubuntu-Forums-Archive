---
title: "Crossover help..."
date: 2005-12-20
forum: General Help
---

### Post by wham on 2005-12-20
I have this file on my desktop; "install-crossover-standard-demo-5.0.0.sh"

What is the easiest way to install this?

---

### Post by Sutekh on 2005-12-20
To install this from a terminal; (and this will be from /home/user/Desktop/ )
```
chmod +x ./install-crossover-standard-demo-5.0.0.sh
sh ./install-crossover-standard-demo-5.0.0
```
I don't know *where* that will install it.  Presumably in the folder you have the .sh file in.  So put it in the folder you want it, say /home/user/crossover/ before you install it.

---

### Post by briancurtin on 2005-12-20
cd Desktop
sudo sh install-crossover-standard-demo-5.0.0.sh

i forget if thats how you handle .sh files or not, also, as Sutkeh just barely beat me to, you need to make sure it has executable permissions

---

### Post by wham on 2005-12-20
Ok, I think I did what I was supposed to except after typing 'sudo sh install-crossover-standard-demo-5.0.0.sh' into the terminal, it seems to go well then a little dialogue pops up with ''$HOME' must exist and belong to you in order for the installation to proceed. You may need to log in as root or use su rather than sudo.' After I click 'OK' it goes back to the terminal.

---

### Post by Ocxic on 2005-12-20
do what it says and try using su instead of sudo

---

### Post by wham on 2005-12-20
When I try su I get this, 'Unknown id: sh'

---

### Post by Ocxic on 2005-12-20
make sure the file is executable with
```

sudo chmod +rx your_file_here
su [enter]
then ./Your_script_here

```

---

### Post by wham on 2005-12-20
That worked great. Thank you!

---

### Post by briancurtin on 2005-12-20
yeah if you are going to use "su" you have to work it differently than using "sudo," so my example was a bit off, but thanks to Ocxic for clearing it up.

---

### Post by shadow07 on 2005-12-20
Well, with Crossover Office, you could have simply executed the installer without su or sudo.  The nice thing about CO is that you can install it under your user account, but CO will only be available for your user account (i.e. if you have other users that access your system with different user accounts, CO will not be available to them.)  That is why you would use su to access the root account without logging out and back in, and install CO.

It also helps to [RTFM]("http://www.codeweavers.com/support/docs/crossover-standard/").

---

