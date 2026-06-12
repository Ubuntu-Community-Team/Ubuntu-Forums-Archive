---
title: "Downgrading Pidgin"
date: 2009-05-08
forum: General Help
---

### Post by Jackelope King on 2009-05-08
I got a little big for my britches and used the information from [this thead](http://ubuntuforums.org/showthread.php?t=613049&highlight=pidgin+compile) to compile Pidgin 2.5.4 from source, which unfortunately caused some issues. Now, since I compiled it from source, I'm at a loss for how to downgrade it or how to uninstall it and then reinstall 2.5.2 from Synaptic. How can I go about removing Pidgin 2.5.4?

---

### Post by zvacet on 2009-05-08
Like thread say

```
sudo aptitude remove pidgin
```

EDIT: you can find Pidgin [here.]("https://launchpad.net/~pidgin-developers/+archive/ppa")

---

### Post by Jackelope King on 2009-05-08
> **zvacet said:**
> Like thread say

```
sudo aptitude remove pidgin
```

EDIT: you can find Pidgin [here.]("https://launchpad.net/~pidgin-developers/+archive/ppa")

I followed this command successfully, removing pidgin. However, after completing the command, Pidgin 2.5.4 still loaded and started just fine, even though it's supposedly been removed!

I'm really starting to feel lost here :(

It now tells me:
```
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
```
Yet when I click on the Pidgin icon in my main menu or in my Cairo dock, Pidgin starts right up again.

What am I doing wrong here?

---

### Post by zvacet on 2009-05-08
Did you use checkinstall as thread advice?If you did then you can find your Pidgin in synaptic.

---

### Post by Jackelope King on 2009-05-08
I had installed checkinstall as per the directions (which I copy/pasted), but honestly, it looks really unfamiliar when I bring it up in the terminal, so it's entirely possible that I didn't do so.

---

### Post by zvacet on 2009-05-08
So how did you do it?Did you look in synaptic to see if Pidgin is there?If it is mark it for complete removal and that should do the job.

---

### Post by Jackelope King on 2009-05-08
> **zvacet said:**
> So how did you do it?Did you look in synaptic to see if Pidgin is there?If it is mark it for complete removal and that should do the job.
Synaptic reports that Pidgin is not installed, and offers no option to uninstall. Neither does using sudo aptitude remove pidgin in terminal (which reports the above code).

And by the way, thanks for the help so far. I've been using Ubuntu for over a year now, but am still pretty weak when it comes to using much beyond the basic GUI interface.

---

### Post by zvacet on 2009-05-09
This should remove it 

```
sudo dpkg --remove --force-remove-reinstreq pidgin
```

---

### Post by Jackelope King on 2009-05-09
> **zvacet said:**
> This should remove it 

```
sudo dpkg --remove --force-remove-reinstreq pidgin
```

This is what I get:
```
:~$ sudo dpkg --remove --force-remove-reinstreq pidgin
sudo: unable to resolve host Soundwave
dpkg - warning: ignoring request to remove pidgin, only the config
 files of which are on the system.  Use --purge to remove them too.
```

---

### Post by zvacet on 2009-05-09
> sudo: unable to resolve host Soundwave

Edit your /etc/hosts file

```
sudo gedit /etc/hosts
```

and you should see first two lines look like 

127.0.0.1 localhost
127.0.1.1 hostname

**hostname = name of your comp**

If you can not use sudo then boot in recovery mode and type

```
nano /etc/hosts
```

and when you correct that file save it and close.Now try again to remove package.

---

### Post by Jackelope King on 2009-05-09
> **zvacet said:**
> Edit your /etc/hosts file

```
sudo gedit /etc/hosts
```

and you should see first two lines look like 

127.0.0.1 localhost
127.0.1.1 hostname

**hostname = name of your comp**

If you can not use sudo then boot in recovery mode and type

```
nano /etc/hosts
```

and when you correct that file save it and close.Now try again to remove package.

I can open the file successfully through the terminal. The first two lines read:

```
127.0.0.1 localhost
127.0.1.1 <computer's name>.Core
```

Should I delete the ".Core" change that to:

```
127.0.0.1 localhost
127.0.1.1 <computer's name>
```

Or is there another correction I'm missing?

---

### Post by zvacet on 2009-05-09
> hould I delete the ".Core" change that to:

Code:
127.0.0.1 localhost
127.0.1.1 <computer's name>

Yes,if that is your comp name.No need for .Core if it is not in your comp name.

---

### Post by brandon88tube on 2009-05-09
May I ask why you are using Pidgin 2.5.4? The newest one and the default one for Jaunty is 2.5.5

---

### Post by Jackelope King on 2009-05-09
> **brandon88tube said:**
> May I ask why you are using Pidgin 2.5.4? The newest one and the default one for Jaunty is 2.5.5

Because I'm currently running Intrepid, for which the default is 2.5.2, and a few months ago when I started fiddling around with it, the newest Pidgin was 2.5.4. ;)

---

### Post by zvacet on 2009-05-09
@ **Jackelope King**

Maybe you want to try newest Pidgin.You can take it from [here.]("http://www.getdeb.net/search.php?keywords=pidgin")

---

### Post by Jackelope King on 2009-05-09
Installed successfully, but the command "pidgin" still brings up 2.5.4, no matter what I do.

Thanks for the help, but I think at this point I need to just throw in the towel and wait a month until I have the time to futz around with a fresh install of Jaunty. For now, 2.5.4 at least is functional, even if the plugins I'd like to use don't work. Ah well.

The moral of the story: if you're going to compile from source, use checkinstall.

---

### Post by zvacet on 2009-05-09
But you told me you used checkinstall.If you didn´t then go to the Pidgin  folder from witch you compile and run

```
sudo make uninstall
```

---

