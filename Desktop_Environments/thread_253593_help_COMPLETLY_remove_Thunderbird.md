---
title: "help COMPLETLY remove Thunderbird"
date: 2006-09-08
forum: Desktop Environments
---

### Post by DougieFresh4U on 2006-09-08
Can some one please tell me how to remove thunderbird from my system and re-install? I have tried to set up 2 differant accounts on thunderbird and these accounts do not have the same password as my linux system. I was never asked for password on one account and on the other it kept asking for my password over & over.So I want to remove completly and reload and start over:confused:

---

### Post by Average Joe on 2006-09-08
I would suggest you completely uninstall the mozilla-thunderbird package and delete your ~/.mozilla-thunderbird directory. That should do the trick.

---

### Post by lagagnon on 2006-09-08
In a terminal:

sudo apt-get remove thunderbird

---

### Post by DougieFresh4U on 2006-09-08
Idid the sudo apt-get remoce thunderbird and it says package thunderbird is not installed so was not removed but add/remove list shows installedand it is in Applications-Internet. I want to completely remove it

---

### Post by aysiu on 2006-09-08
Paste these commands into the terminal. If you get errors, that's okay. ```
mv ~/.mozilla-thunderbird ~/.mozilla-thunderbird.old
sudo aptitude remove mozilla-thunderbird
sudo aptitude update
sudo aptitude install mozilla-thunderbird
```

---

### Post by arkangel on 2006-09-08
all your data concerning  the thunderbird is located in a directory .thunderbird  remove it will solve your problem, in a terminal type

rm -rf ~/.thunderbird

---

### Post by aysiu on 2006-09-08
Just to clarify a bit...

If you're using *Ubuntu*'s Thunderbird, then your settings will be in /home/dougie/.mozilla-thunderbird

If you're using *Mozilla*'s Thunderbird, then your settings will be in /home/dougie/.thunderbird

---

### Post by DougieFresh4U on 2006-09-08
I pasted what said and removed and got no errors. Now I would like to re-load & set-up. I would like to know why it did not want passwords from other e-mail accounts and I do not know how to re-load thunderbird. I was very lost with evolution. by the way, thanks so much

---

### Post by aysiu on 2006-09-08
Well, if you pasted *all* the commands I gave, you have already reinstalled it. Just go ahead and go to Applications > Internet > Thunderbird and set things up again.

---

### Post by DougieFresh4U on 2006-09-08
ok it recieved mail but when I go to send mail I get erroe - smtp server may be unavail or nort accepting please check smtp settings they are the correct settings

---

### Post by brucevangeorge on 2006-09-08
> **arkangel said:**
> all your data concerning  the thunderbird is located in a directory .thunderbird  remove it will solve your problem, in a terminal type

rm -rf ~/.thunderbird


This did not work. Shoudl there be sudo or something before this? Or do I just copypaste into the terminal?

---

### Post by DougieFresh4U on 2006-09-08
Thanks "aysiu". I got it together and I'm good to go!!  Any one of a way to get the smileys and such on Thunderbird? I have Smiley Central and Fun Cards on my other machine that has WinXP.

---

### Post by arkangel on 2006-09-09
> **aysiu said:**
> Just to clarify a bit...

If you're using *Ubuntu*'s Thunderbird, then your settings will be in /home/dougie/.mozilla-thunderbird

If you're using *Mozilla*'s Thunderbird, then your settings will be in /home/dougie/.thunderbird

if you  have installed the thunderbird that you find in the repositories use the first one to erase the configuration files: 
rm -rf ~/.mozilla-thunderbird

On the other hand , if you have installed the thunderbird on your own as i did  use the second one to erase the configuration files:  
rm -rf ~/.thunderbird

no sudo needed, because you have full access and rights in your own profile-home directory , although it will work anyway

---

