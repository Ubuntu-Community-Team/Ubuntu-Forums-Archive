---
title: "Please Help for installing Compiz Fusion"
date: 2008-03-08
forum: Desktop Effects &amp; Customization
---

### Post by s_merd on 2008-03-08
Hi Friends,
I am really new for ubuntu.

I ve tried to install compiz fusion and followed these steps :

[http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml](http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml)

but i got some problems.
when i closed the Software Sources window,

[IMG]http://img156.imageshack.us/img156/5936/0002km9.jpg[/IMG]
[IMG]http://img523.imageshack.us/img523/3263/0003tv1.jpg[/IMG]
[IMG]http://img72.imageshack.us/img72/2306/0004ll8.jpg[/IMG]

and 
in the terminal, after this;

**sudo apt-get update**

I ve got ;

**E: Malformed line 59 in source list /etc/apt/source.list (dist parse)**

Now What should I do?

Help me.

---

### Post by 22flames on 2008-03-08
you already have it it comes installed you need the effects manager go to applecations add remove and serch ccsm than go to system preferances apperance effects tab custom than click preferances button

---

### Post by dyoung on 2008-07-16
> **22flames said:**
> you already have it it comes installed you need the effects manager go to applecations add remove and serch ccsm than go to system preferances apperance effects tab custom than click preferances button

When i attempt to open the add/remove it get the following error.  'EL Mlaformed line 56 in source list /ect/apt/source.list (absolute dist) E: the list of sources could not be read. I am trying to get the compiz shpere install (very new to linux/ubuntu) thanks

---

### Post by overdrank on 2008-07-16
> **dyoung said:**
> When i attempt to open the add/remove it get the following error.  'EL Mlaformed line 56 in source list /ect/apt/source.list (absolute dist) E: the list of sources could not be read. I am trying to get the compiz shpere install (very new to linux/ubuntu) thanks

Hi and you are posting the forum archive, you will need to edit your source list and correct the issue with line 56. Use the command ```
gksudo gedit /etc/apt/sources.list
``` and if you will look at the link in my signature on desktop effects it will help also. :)

---

### Post by dyoung on 2008-07-16
when i do the line you posted get nothing but a blank page ?

---

### Post by overdrank on 2008-07-16
> **dyoung said:**
> when i do the line you posted get nothing but a blank page ?

Hi and are you sure you are typing it correctly?  I would suggest copy and paste and then no mistakes.

---

### Post by dyoung on 2008-07-16
this is line 56 (at least i think it is there not numbered so when i put 56 in the search this is the bottom line displayed)  deb-src [http://ppa](http://ppa). launchpad.net/ compiz/ ubuntu hardy main
 When i try to open the add/remove i the following error " mafor faliure software mgt. systerm check broken package with synaptic check file permission and correctness of file /ect/apt/source.list relaod software sudo apt-get and sudo apt-get insall -f "
 when i do the apt-get is when i get the error message about line 56. 
 Thanks for your help. (totally new and trying to learn ubuntu)

---

### Post by m_duck on 2008-07-16
it looks like there is a space between "ppa." and "launchpad" in that line

remove that and save it and it should get rid of your line 56 error

there also seems to be a space between ".net/" and "compiz/" which will need removing

---

### Post by dyoung on 2008-07-16
> **m_duck said:**
> it looks like there is a space between "ppa." and "launchpad" in that line

remove that and save it and it should get rid of your line 56 error

there also seems to be a space between ".net/" and "compiz/" which will need removing

Great that worked. can you tell me how to get the sphere installed and working ?

---

### Post by m_duck on 2008-07-16
I've not actually done this myself and am not that up with all the crazy compiz coolness! From some googling, what is the result in the terminal when you type:

```
compiz --version
```in the terminal?

From [http://technalizer.com/TuxCentre/tag/compiz-fusion/](http://technalizer.com/TuxCentre/tag/compiz-fusion/) it seems that you must have at least Compiz 0.7.6.

Once you have the right version if you run (alt + F2) "ccsm" and look for the "Cube Reflection and Deformation" plugin, there are options there to hopefully get the effect you want..

As I said, I have not done this myself so apologies if this does not work.

---

