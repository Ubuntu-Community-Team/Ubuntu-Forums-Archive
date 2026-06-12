---
title: "How to install Midnight Commander"
date: 2009-05-15
forum: General Help
---

### Post by hcchen on 2009-05-15
As a new Linux user, the first thing to me is to find a Norton Commander clone. I found the name "Midnight Commander" and then have found it very difficult to install or enable. (I use Ubuntu 710). 

What I have done (all failed) are , (don't read them, very frustrated, just teach me how did you install mc? thank you !!!! )

[FONT=courier new, courier, mono]hcchen@hcchen-laptop:/$ mc 
The program  'mc' is currently not installed. You can install it by typing: 
sudo apt-get  install mc 
You will have to enable component called 'universe' 
bash: mc:  command not found 

[/FONT]So I search the Internet learned and enable 'universe' this way 
[FONT=courier new, courier, mono]Click on "System" ->  "Administration" -> "Software Sources".
[/FONT][FONT=courier new, courier, mono]On the  "Ubuntu Software" tab look for the line that contains "(universe)". Make sure  the check box next to that line is checked.
[/FONT]
Then try again,
hcchen@hcchen-laptop:/mnt/share/mc-4.6.1$  sudo apt-get install mc
Reading package lists... Done
Building dependency  tree       
Reading state information... Done
E: Couldn't find package mc   [COLOR=Red]<====== 'universe' enabled but mc is still not found.[/COLOR]
[FONT=courier new, courier, mono]
[/FONT]I also tried to download mc from the official site. [FONT=arial, helvetica, sans-serif][SIZE=3][COLOR=#0000ff][http://www.midnight-commander.org/](http://www.midnight-commander.org/)  [/COLOR][/SIZE][/FONT]but it provides only source. No executable. When I walk through all the way to build mc-4.6.2.tar.gz , I found that I have to install glib. 

When trying to install glib 2.10.3 , I got blocked again at
[COLOR=#666666][FONT=courier new, courier, mono][FONT=arial, helvetica, sans-serif][FONT=Verdana, Arial, Helvetica, sans-serif]sudo ./configure <====  When I  did this , I got ...
[/FONT]... snip .....
[/FONT]checking libintl.h  usability... yes
checking libintl.h presence... yes
checking for  libintl.h... yes
checking for ngettext in libc... yes
checking for  dgettext in libc... yes
checking for bind_textdomain_codeset...  yes
checking for msgfmt... no
configure: error:
*** You must have  either have gettext support in your C library, or use the
*** GNU gettext  library. ([/FONT][[FONT=courier new, courier, mono]http://www.gnu.org/software/gettext/gettext.html[/FONT]]("http://www.gnu.org/software/gettext/gettext.html")[/COLOR]   [COLOR=#666666][FONT=courier new, courier, mono]rm: cannot remove  `*.core': Protocol error
[/FONT][FONT=courier new, courier, mono]hcchen@hcchen-laptop:/mnt/share/glib-2.10.3$[/FONT][FONT=courier new, courier, mono] 
[/FONT][/COLOR]


[COLOR=#666666][FONT=courier new, courier, mono]And now I give up !![/FONT][/COLOR]


[COLOR=#666666][FONT=courier new, courier, mono]Why so many people are using MC but only me who can't walk through just installation?[/FONT][/COLOR]


[COLOR=#666666][FONT=courier new, courier, mono]
[/FONT][/COLOR]

---

### Post by kerry_s on 2009-05-15
when you change the repo's you need to run> 
**sudo apt-get update**
then you can try:
**sudo apt-get install mc**

if you use synaptic, which is the gui, it would have told you that you need to reload.

---

### Post by kerry_s on 2009-05-15
my bag i just saw the the ubuntu 7.10, that is no longer supported, those repo's are gone. you need to update to a newer ubuntu version.

---

### Post by hcchen on 2009-05-15
Hi thank you all !
I tried Ubuntu 804 ,  type mc and simply follow the instructions can install it successfully.

I remember when I enabled the 'universe' something on my Ubuntu 710, something like '404 not found' appears that says the reload is not completed. This is one possible reason. And, I also noticed my 710's 'universe' and friends are NOT checked by default while my 804 checks them all. 

Midnight Commander look and feel is totally like our old buddy Norton Commander that helps Linux beginner so much .

---

### Post by albinootje on 2009-05-15
> **hcchen said:**
>  I tried Ubuntu 804 ,  type mc and simply follow the instructions can install it successfully.

Good :)
> 
I remember when I enabled the 'universe' something on my Ubuntu 710, something like '404 not found' appears that says the reload is not completed. This is one possible reason. 

Ubuntu 7.10 has reached end of life, that's why, see here :
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Greetings from a (more than 10 years) happy Midnight Commander user! :)

---

### Post by hcchen on 2009-05-24
Now I found 'X file explorer' XFE is most useful to me. 
XFE is also a Norton Commander clone for Linux. Graphics interface so it's more like Windows Commander or Total commander. 

I actually found a lot of Norton commander friends on Wikipedia. Google all above names brings you to comparison pages (there are many on the net!). XFE seems good so I tried and found I like it. It's small and very like Windows file manager but with two columns of file list.

How to install XFE on Ubuntu:
1. open terminal
2. type 'xfe'
3. follow the instructions. use 'sudo' in front of command line to get root permission for installation.
4. after all type xfe to run.

enjoy it ~~~~

---

### Post by directhex on 2009-05-25
Ubuntu 7.10 is dead. If you want to continue using it (with no security etc support) then you need to change your mirror from whatever youre using right now to old-releases.ubuntu.com

You can't find packages because 7.10 is dead.

---

