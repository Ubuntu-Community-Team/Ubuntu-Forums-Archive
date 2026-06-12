---
title: "Cairo-Dock clock and dustbin theme couldn't be found"
date: 2010-02-06
forum: Desktop Environments
---

### Post by IanVaughan on 2010-02-06
On launching Cairo-Dock (from either the "Cairo-Dock (no OpenGL)" or "GLX-Dock")
I get 2 error boxes shown :-
clock : the theme couldn't be found ...
dustbin

I read about trying the following, but no talk of what to do if this fails:

> ian@Bart:~$ wget [http://themes.cairo-dock.org/liste.txt](http://themes.cairo-dock.org/liste.txt)
--2010-02-06 20:04:25--  [http://themes.cairo-dock.org/liste.txt](http://themes.cairo-dock.org/liste.txt)
Resolving themes.cairo-dock.org... failed: Name or service not known.
wget: unable to resolve host address `themes.cairo-dock.org'

ian@Bart:~$ wget "http://themes.cairo-dock.org/themes/liste.txt" -O "/tmp/cairo-dock-net-file.WDY6eR" -t 2 -T 5
--2010-02-06 20:04:47--  [http://themes.cairo-dock.org/themes/liste.txt](http://themes.cairo-dock.org/themes/liste.txt)
Resolving themes.cairo-dock.org... failed: Connection timed out.
wget: unable to resolve host address `themes.cairo-dock.org'


---

### Post by hariks0 on 2010-02-06
I too face the same problem. Just select the no 'x' in the prompt. It will continue.

---

### Post by fabounet on 2010-02-07
You have to install the latest version (2.1.3)
availabe on Launchpad : :
[https://launchpad.net/~cairo-dock-team/+archive/ppa]("https://launchpad.net/~cairo-dock-team/+archive/ppa")

---

### Post by agkq62 on 2010-02-07
I am being very thick. I have downloaded the new version but now don't seem to have any new icons to choose from. On startup a message appears no plugins installed.

---

### Post by fabounet on 2010-02-08
you have to follow the instructions, not to download the tarballs ;-)
it's all automatic then.

---

### Post by agkq62 on 2010-02-08
I did follow the instructions under "PPA Description". What did i do wrong.

Thanks.

---

### Post by fabounet on 2010-02-08
maybe when you copied the command you didn't notice the 2nd one is very long and appears on the site on 2 lines
It's actually a single command line.
```
echo "deb http://ppa.launchpad.net/cairo-dock-team/ppa/ubuntu $(lsb_release -sc) main ## Cairo-Dock-PPA" | sudo tee -a /etc/apt/sources.list
```
it's only a guess though, you should check in the end of your /etc/apt/sources.list that everything looks correct.

---

### Post by agkq62 on 2010-02-08
Thanks getting somewhere, now got the dustbin but still clock problems. The clock details are showing in the config page but  as before just the date is showing on the dock.

Any ideas, thanks.

---

### Post by fabounet on 2010-02-09
in the Clock config you can choose to display the date on the icon or not.
also you can choose between a numerical rendering or an analogical one (which has many themes).
Hope this helps.

---

### Post by agkq62 on 2010-02-09
The problem is the clock face isn't showing only the date

---

### Post by agkq62 on 2010-02-09
Just found out if I restart with the clock active I get a warning message " clock, the theme could not be found"

---

### Post by agkq62 on 2010-02-14
Anyone???  I would love to get the clock working.

---

### Post by rahilm on 2010-02-14
what version of cairo-dock are you using??

---

### Post by agkq62 on 2010-02-14
Version 2.1.3.2.1ubuntu1-karmic (cairo-dock-core}

---

### Post by fabounet on 2010-02-14
ok, are you under a proxy or with no internet connection ?

anyway you can just right-click on the clock icon -> configure this applet, then select another theme.

---

### Post by agkq62 on 2010-02-14
What ever theme I choose the message comes up "theme could not be found.

I am on a broadband internet connection.

---

### Post by rahilm on 2010-02-15
so lets see all the possibilities....
when I had installed cairo-dock , i was facing the EXACT same problem. So, I did a little research here and there and found out that cairo-dock needs to be connected to "cairo-dock.org" to get the themes. But the site was down at that time (and it is till now i suppose), so a fellow forum member suggested me to launch cairo-dock using the following command:
```
cairo-dock -S http://themes.cairo-dock.vef.fr
```..It will solve your problem..
I have cairo-dock 2.4.1-0 alpha0, in which they put this by deafult..

so either you can upgrade to the current version (i use the weekly ppa).. or you can configure the cairo-dock launcher from the menu to the above line..

Here is the link to the thread:
[http://ubuntuforums.org/showthread.php?t=1371836&page=2](http://ubuntuforums.org/showthread.php?t=1371836&page=2)


Reply if you succeed

---

### Post by fabounet on 2010-02-15
the 2.1.3 already has the correct address though.
also, if you're seeing the themes in the list, it means the connection is ok.
so maybe it's a permission problem, try a "chmod -R 777 ~/.config/cairo-dock"

---

### Post by ghostsounds on 2010-02-17
Hi, I'm a n00b to the forums here, but I was having identical problems and I managed to find a solution after some poking around. Hopefully it will work for others.

What I did is right click on the dustbin, select "configure this applet", go to the Module tab in the configuration menu, under theme there's an option of "Choose one of the available themes" click the dropdown menu and select "(Local) Default". 
For clock you do the same thing to configure the applet and go to Module, but this time you have to click the "Analogic View" menu within Module and then click the "List of available themes for the analogic display" dropdown. 
It seems as though the default theme for those applets are present, but you need to choose them manually to make it work. Choosing the default for both the dustbin and clock resolved the issue for me completely.

---

### Post by agkq62 on 2010-02-20
Finally got somewhere, tried opening Cairo-dock with "no OpenGL" and everything worked.

Thanks all for your input

---

### Post by youngdaddytc on 2010-03-10
> **ghostsounds said:**
> Hi, I'm a n00b to the forums here, but I was having identical problems and I managed to find a solution after some poking around. Hopefully it will work for others.

What I did is right click on the dustbin, select "configure this applet", go to the Module tab in the configuration menu, under theme there's an option of "Choose one of the available themes" click the dropdown menu and select "(Local) Default". 
For clock you do the same thing to configure the applet and go to Module, but this time you have to click the "Analogic View" menu within Module and then click the "List of available themes for the analogic display" dropdown. 
It seems as though the default theme for those applets are present, but you need to choose them manually to make it work. Choosing the default for both the dustbin and clock resolved the issue for me completely.
  
this worked perfectly, thank you.  with all the options they have, it's hard to find the ones you need.  thanks again.

---

### Post by Lokesh123 on 2010-03-22
> **ghostsounds said:**
> Hi, I'm a n00b to the forums here, but I was having identical problems and I managed to find a solution after some poking around. Hopefully it will work for others.

For clock you do the same thing to configure the applet and go to Module, but this time you have to click the "Analogic View" menu within Module and then click the "List of available themes for the analogic display" dropdown. 
It seems as though the default theme for those applets are present, but you need to choose them manually to make it work. Choosing the default for both the dustbin and clock resolved the issue for me completely.

I am having the same problem with the clock, resulting in crash of the whole system. I installed cairo-dock twice, first through synaptic package manager and then the most recent version through PPA. In both cases the clock caused trouble.

It turned out there is no .cairo-dock directory in home (or elsewhere). When I followed the above steps I discovered there is no analog theme installed but the anolog view is selected. Changing to the digital view made it.

This is weird, it should be a common problem because it comes through standard installation. 

Cheers,
Lokesh

---

