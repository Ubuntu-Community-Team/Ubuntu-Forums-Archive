---
title: "GIMP wont start!"
date: 2009-06-07
forum: General Help
---

### Post by Marce Acosta on 2009-06-07
Well, my problem is the following: I use ubuntu 9.04, and last week, I wanted to make a good-looking image for my blog, BUT, I went to the apps menu, graphics, clicked on gimp, and it took a time, mouse showed like loading, and GIMP didn't start. I tried going to the terminal and typing gimp, but, instead of opening GIMP, It opened GIMP's installer, I reinstalled it, and it opened. Later on, I wanted to use GIMP again. I went to the menu and clicked on it. It did not open ](*,).. What should I do?
 
thanks for the help ;)

---

### Post by michy99 on 2009-06-07
did you try from the terminal again? Did you get the same result?

---

### Post by Marce Acosta on 2009-06-07
> **michy99 said:**
> did you try from the terminal again? Did you get the same result?
 yes, I did. Like 3 times.. any other idea?

---

### Post by michy99 on 2009-06-07
So just to be clear, when you try to run from terminal, you have to install it again? By any chance are you running from a Live CD?

---

### Post by Marce Acosta on 2009-06-07
> **michy99 said:**
> So just to be clear, when you try to run from terminal, you have to install it again? By any chance are you running from a Live CD?
 yes, I have to install it again, and no, I have ubuntu installed in my computer.

---

### Post by michy99 on 2009-06-07
Can you try to start from terminal and post exactly what it says?

---

### Post by Marce Acosta on 2009-06-07
> **michy99 said:**
> Can you try to start from terminal and post exactly what it says?
 It doesn't say anything, It just opens a window that says: this is the GIMP installer..

---

### Post by michy99 on 2009-06-07
In your home folder is a hidden folder named .gimp-2.6. Delete it and try to start gimp again.

---

### Post by Marce Acosta on 2009-06-07
ok.. I will..

---

### Post by Marce Acosta on 2009-06-07
> **michy99 said:**
> In your home folder is a hidden folder named .gimp-2.6. Delete it and try to start gimp again.
I tried running it from the menu: nothing
I also tried from the terminal, window opens, BUT it is GIMP 2.2, not 2.6

---

### Post by michy99 on 2009-06-07
The only thing I can think to try is uninstall and install again.```
sudo apt-get remove gimp
sudo apt-get inastall gimp
```

---

### Post by Marce Acosta on 2009-06-07
> **michy99 said:**
> The only thing I can think to try is uninstall and install again.```
sudo apt-get remove gimp
sudo apt-get inastall gimp
```
oook.. I'll try that.. thanks..

---

### Post by Marce Acosta on 2009-06-07
I need more ideas.. but thanks.. it didn't work.. Do you have any other idea? If it doesn't work, I'll make a backup of my stuff and re-install ubuntu.. (wich I REALLY don't wanna do)

---

### Post by michy99 on 2009-06-07
I mis-spelled 'install' in my previous post. I hope you caught that. If that doesn't work I'm out of ideas.

---

### Post by Marce Acosta on 2009-06-09
> **michy99 said:**
> I mis-spelled 'install' in my previous post. I hope you caught that. If that doesn't work I'm out of ideas.
Yeah.. I noticed it.. I corrected it, but nothing.. I REALLY need GIMP for many things.. thanks

---

### Post by unutbu on 2009-06-09
Marce, it sounds like you have an old version of gimp on your machine.
Please post the output of 

```

dpkg --get-selections | grep gimp   # This lists all gimp packages installed on your machine
which gimp                          # shows path to the gimp program 
$(which gimp) --version             # shows the version of gimp
ls -l /usr/bin/gimp*                # lists all gimp files in /usr/bin
apt-cache policy gimp               # shows which gimp package APT knows about
ls -lad ~/.gimp*                    # Lists the .gimp dirs in your home directory
lsb_release -a                      # shows which version of Ubuntu you are running

```

---

### Post by route53 on 2009-06-10
I too have an inactive Gimp, says its starting, disappears.
Re-installed a few times, no go.

---

### Post by Marce Acosta on 2009-06-10
> **unutbu said:**
> Marce, it sounds like you have an old version of gimp on your machine.
Please post the output of 

dpkg --get-selections | grep gimp  


 gimp                     install
gimp-data                    install
gimp-data-extras                install
gimp-dds                    install
gimp-help-common                install
gimp-help-en                    install
gimp-help-es                    install
gimpshop                    install
libgimp2.0                    install


That's the first thing

---

### Post by Marce Acosta on 2009-06-10
> **unutbu said:**
> Marce, it sounds like you have an old version of gimp on your machine.
Please post the output of 

which gimp      /usr/local/bin/gimp


That's the second thing

---

### Post by Marce Acosta on 2009-06-10
> **unutbu said:**
> Marce, it sounds like you have an old version of gimp on your machine.
Please post the output of 

$(which gimp) --version    Versión de El Gimp 2.2.11


The third thing

---

### Post by Marce Acosta on 2009-06-10
> **unutbu said:**
> Marce, it sounds like you have an old version of gimp on your machine.
Please post the output of 
          
ls -l /usr/bin/gimp*


result=



   lrwxrwxrwx 1 root root       8 2009-06-07 22:17 /usr/bin/gimp -> gimp-2.6
-rwxr-xr-x 1 root root 4345608 2009-03-17 05:53 /usr/bin/gimp-2.6
lrwxrwxrwx 1 root root      16 2009-06-07 22:17 /usr/bin/gimp-console -> gimp-console-2.6
-rwxr-xr-x 1 root root 2131856 2009-03-17 05:53 /usr/bin/gimp-console-2.6

---

### Post by unutbu on 2009-06-10
Marce,
You have two versions of gimp installed. Gimp version 2.2.11 is located at /usr/local/bin/gimp. This might be gimpshop.

You also have Gimp version 2.6 installed at /usr/bin/gimp.

What happens when you open a terminal and type /usr/bin/gimp?
I think there is a fair chance Gimp will start for you then.

If it does, and you like it, then the next question might be, how to get rid of the non-functioning Gimp version 2.2.11 located at /usr/local/bin/gimp.

Is this one installed by gimpshop? If you are willing to get rid of gimpshop, type
```

sudo dpkg --purge gimpshop
```

---

### Post by Marce Acosta on 2009-06-10
> **unutbu said:**
> Marce,
You have two versions of gimp installed. Gimp version 2.2.11 is located at /usr/local/bin/gimp. This might be gimpshop.

You also have Gimp version 2.6 installed at /usr/bin/gimp.

What happens when you open a terminal and type /usr/bin/gimp?
I think there is a fair change gimp will start for you then.

If it does, and you like it, then the next question might be, how to get rid of the non-functioning Gimp version 2.2.11 located at /usr/local/bin/gimp.

Is this one installed by gimpshop? If you are willing to get rid of gimpshop, type
```


sudo dpkg --purge gimpshop
```

yes.. it's gimp shop.. I didn't know it would gimme so much trouble.. thank you very much.. I'll try what you told me to do

---

### Post by Marce Acosta on 2009-06-10
Thank you so much! you REALLY solved my problem! when I uninstalled gimpshop, gimp worked.. thanks!

---

### Post by Lynpy on 2009-06-22
I have been having the same problem (brickwall smilie most appropriate), I shall try your fix, thanks.

---

