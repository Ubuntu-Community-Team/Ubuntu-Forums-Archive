---
title: "Matlab R2011a icon not working in the Unity Launcher (11.04 - 64bit)"
date: 2011-05-02
forum: Education &amp; Science
---

### Post by Blitz Tungsten on 2011-05-02
I've just installed MATLAB R2011a (64bit version) in the latest Ubuntu 11.04 (obviously 64bit as well).

I've followed this [http://thameera.wordpress.com/2010/10/21/installing-matlab-2008a-on-ubuntu-10-10/]("guide") for the installation part.

Then after running Matlab for the first time with the command:

```
sh /usr/local/matlab/bin/matlab
```

I right-clicked on the Unity Launcher to add Matlab, but after logging off it disappeared from there.

Then from Ubuntu help I've tried:

1. Get an icon:

```
sudo wget http://upload.wikimedia.org/wikipedia/commons/2/21/Matlab_Logo.png -O /usr/share/icons/matlab.png
```

2. Get the launcher file:

```
sudo wget 'https://help.ubuntu.com/community/MATLAB?action=AttachFile&do=get&target=matlab-r2011a.desktop' -O /usr/share/applications/matlab.desktop
```

The icon remains there after closing Matlab, but I've yet to log-off or restart.

The problem is that when I click on it, it does nothing!

So to open Matlab I've always to type in terminal:

```
sh /usr/local/matlab/bin/matlab
```

Did any of you succeed in putting a working icon of Matlab in the brand new Unity Launcher?

Thanks in advance!

---

### Post by chfarges on 2011-05-07
Hello,

I have the same problem. Did you find something to fix it?

Thanks!

---

### Post by Blitz Tungsten on 2011-05-09
Nope, I'm still looking for a solution!

---

### Post by martinianom on 2011-05-09
I have the same problem!, on top of that, I feel that it makes my system much less stable. 

I use an extra monitor at work and it gets really unstable when trying to move the Matlab icon on the unity bar and/or simply trying to have it as a permanent icon.

---

### Post by hooger_booger on 2011-05-10
I had the same problem when using the right click -> keep on launcher option. But then I tried dragging it from the dash to the launcher (before it was running) and it stays there now. Hope this helps.

---

### Post by Blitz Tungsten on 2011-05-10
> **hooger_booger said:**
> I had the same problem when using the right click -> keep on launcher option. But then I tried dragging it from the dash to the launcher (before it was running) and it stays there now. Hope this helps.

The icons stays there, but I can't open Matlab from it!

Which procedures have you followed to install Matlab?

---

### Post by hooger_booger on 2011-05-10
Was it working before you moved it to the launcher?

I should probably have mentioned that I am still using 2010a, I followed these:

[https://help.ubuntu.com/community/MATLAB/R2010a](https://help.ubuntu.com/community/MATLAB/R2010a)

But the 2011a ones are here: 

[https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB)

After that I had the error message described and solved here:

[http://morganbye.net/blog/2011/05/matlab-ubuntu-1104](http://morganbye.net/blog/2011/05/matlab-ubuntu-1104)

 Good luck!

---

### Post by Blitz Tungsten on 2011-05-10
I solved the problem!

After uninstalling and reinstalling Matlab (useless operation), I logged on Gnome, then after searching for a while I found this 3d: [http://ubuntuforums.org/showthread.php?t=1416028](http://ubuntuforums.org/showthread.php?t=1416028)

I followed users' suggestions, then Matlab was working perfectly on Gnome.

I switched back to Unity, I dropped the Matlab icon from Dash and now works perfectly!

Thanks again!

---

### Post by brain270 on 2011-10-10
Hey guys,
I was having that problem. I'm not very experienced in ubuntu, but I solved like this:
1- create a launcher on desktop
2- select run application on terminal
3- command: sudo /usr/local/MATLAB/R2011A/bin/matlab (change matlab directory to yours)

after this I placed that launcher on the unity bar. The problem I still couldn't solve is that I can't remove the launcher form the desktop without loosing the one on the unity bar.
Any thoughts?

Thanks

---

### Post by PC_load_letter on 2011-10-11
If the issue is removing the launcher form the desktop, just put the launcher (or create a new one and redo the process) in your home folder instead.

---

### Post by beew on 2011-11-16
The tip from Ubuntu help works (first post) But instead of keeping the icon in the launcher after you open matlab with the command you should open /usr/share/applications/ and drag the file matlab.desktop to the Unity launcher bar.

BTW, the command to start matlab in the terminal is simply```
 matlab
```, no need for sh or specifying the complete path or sudo.

Also note that the command to start matlab in the .desktop file downloaded with the Ubuntu help tip is ```
matlab -desktop
```, instead of just ```
matlab 
```, this is rather peculiar, I have created manually a .desktop file with the command "matlab" and put it in .local/share/applications then drag it to the launcher, when clicked matlab opened and then crashed, but "matlab -desktop" works.

---

### Post by abalter on 2012-07-30
This totally worked for me:

[https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB)

But I'm usign XFCE

---

