---
title: "Disable Mutter to enable back Compiz Fusion?"
date: 2010-12-14
forum: Desktop Environments
---

### Post by Rushyang on 2010-12-14
Hiya fellas!

I updated system few days back. and Ka-boom! Suddenly my all desktop effects gone. My theme effects of Mac from the theme Macubuntu 10.10 were gone too. I removed Macubuntu and tried to go into visual effects tab in Appearance Preferences, but it says "Mutter is running, Can't switch to other effects." 

Now, may this mutter is coming in natty narwhal & new, but seriously it's 2D effects aren't smooth enough.. Also I just can't use Alt+Tab which I'm habitual of. 

My question is: How to disable this mutter and re-enable my Compiz-Fusion? 

PS: I tried to kill mutter process from the daemons and start a compiz.. It didn't work.. Instead, I had to reboot my machine everytime I did that. When I remove mutter from 

sudo apt-get remove mutter..

My desktop stays blank after a reboot and I can't access anything.. Thanks to EasyStroke that I'd given stokes to open a new terminal.

---

### Post by stinkeye on 2010-12-14
Try 
```
compiz --replace
```

---

### Post by Rushyang on 2010-12-14
As you suggested I tried it.. and here is my terminal message.
> rushyang@rushyang-MS-7519: ~ $ compiz --replace
Starting gtk-window-decorator
compiz: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_property_to_quads


---

### Post by stinkeye on 2010-12-14
Are you using fusion-icon?

```
sudo apt-get install fusion-icon
```

All I did was enter 
```
mutter --replace &
```
to test

and 
```
compiz --replace &
```
to switch back

Possibly try using fusion-icon to switch to compiz.

and check you have all your compiz packages 
```
sudo apt-get install compiz compiz-plugins compiz-gnome compiz-core compiz-fusion-plugins-main compiz-fusion-plugins-extra fusion-icon compizconfig-settings-manager
```

---

### Post by stinkeye on 2010-12-14
Check in the software centre what version of libdecoration0 you have.
Mine is```
1:0.8.6-0ubuntu9.1
```

 You may have packages from other repos you have enabled for unity or compiz.
If so you need to disable the repo and uninstall/reinstall the compiz packges.

---

### Post by Rushyang on 2010-12-14
Stinkeye,

Perhaps, I got the broken packages error from my repo update.. Here is my [pastebin]("http://paste.ubuntu.com/543610/") of trying to install compiz... I did try to reinstall compiz before I posted.. Just forgot to mention it. Sorry for that.

Here is my [repository..]("http://paste.ubuntu.com/543616/") 

My Compiz Window Decoration Library is on...
1:0.9.2.1+glibmainloop-0ubuntu2~maverick1 (libdecoration0)
Last updated on 9th Dec.

& yes, I highly appreciate your help. :)

---

### Post by stinkeye on 2010-12-14
Is there any reason you have these repos enabled.
```
deb http://security.ubuntu.com/ubuntu maverick-proposed main restricted universe multiverse
deb http://fi.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
```
They are not enabled by default although I dont think they contain compiz related packages.

Did you enable the unity repo which contains some updated compiz packages?
It doesn't appear to be listed now.

Any way, check versions of compiz related packages(see pic) because this 
package **1:0.9.2.1+glibmainloop-0ubuntu2~maverick1 (libdecoration0)**
is a different version than mine.

Open synaptic and search for compiz.(click on the "s" in the bar to group the packages by status)
If any packages are different you can downgrade by going to [B]package > force version
[/B] and choose from the dropdown.

Next time you update look for compiz updates coming from outside the default repos.

---

### Post by Rushyang on 2010-12-15
I downgraded my compiz version to  1:0.8.6 from Symantic Package Manager..

Yes, I installed unity .. when we do it comes with mutter and afterwards it's all problematic. because uninstalling it doesn't work either. Also, I think I didn't enable any repo, because installing unity just take one command..
> sudo apt-get install unity
Do you think, changing repos and update with it might work? Is that so, then I would like to replace my repo file with yours after a backup...

---

### Post by stinkeye on 2010-12-15
So do all your compiz packages match what I have including
```
libdecoration0   1:0.8.6-0ubuntu9.1
libdecoration0-dev     1:0.8.6-0ubuntu9.1
```

> Yes, I installed unity .. when we do it comes with mutter and afterwards it's all problematic. because uninstalling it doesn't work either. Also, I think I didn't enable any repo, because installing unity just take one command..
I dont think unity or mutter are your problem as I just remembered I tried
Unity and it is still installed on my system along with mutter.

---

### Post by stinkeye on 2010-12-15
Try this.

First of all disable the maverick-backports and maverick-proposed ppas unless
you have them enabled for a specific reason.
Synaptic package manager > settings > repositories > updates

Install ppa-purge
```
sudo apt-get install ppa-purge
```

Install the compiz ppa.
This wont upgrade any packages.
Just enables ppa-purge to make a list of packages to downgrade.
```
sudo add-apt-repository ppa:compiz/ppa && sudo apt-get update
```


Then purge the compiz ppa to downgrade packages.
```
sudo ppa-purge ppa:compiz/ppa
```
You should see something like this
```
glen@MavMusic:~$ sudo ppa-purge ppa:compiz/ppa
PPA to be removed: compiz ppa
Package revert list generated:
 compiz/maverick compiz-core/maverick compiz-dev/maverick compiz-gnome/maverick 
compiz-plugins/maverick libcompizconfig0/maverick libdecoration0/maverick 
libdecoration0-dev/maverick
```

---

### Post by checoimg on 2011-02-24
I followed stinkeyes instructions and afetr that I right clicked on compiz fusion icon and choose reload window manager. But the panel is lost.

---

### Post by checoimg on 2011-02-24
I the end you have what you are asking for. When you login it has mutter but just click "reload windows manager" and switch to compiz to switch back log out and log in. I use AWN and Gnome do so I don't need the panel maybe a notification area

---

### Post by kerry_s on 2011-02-24
in 10.10 that unity is made from mutter, not compiz, so mutter is the desktop.

so if your using netbook edition, log out & select desktop to get a standard desktop.

---

### Post by Murdock Ruml on 2011-02-24
> **kerry_s said:**
> in 10.10 that unity is made from mutter, not compiz, so mutter is the desktop.

so if your using netbook edition, log out & select desktop to get a standard desktop.

are you saying that the notepad edition can not run compiz. I have the notepad edition on my laptop and am trying to get the Cube. am I am having no luck. I just installed this OS and have not yet started to personalise it, so if I have to switch operating systems now would be the time to do it.

---

### Post by kerry_s on 2011-02-25
> **Murdock Ruml said:**
> are you saying that the notepad edition can not run compiz. I have the notepad edition on my laptop and am trying to get the Cube. am I am having no luck. I just installed this OS and have not yet started to personalise it, so if I have to switch operating systems now would be the time to do it.

yes, it's better you just grab the desktop version, if you want to use effects & customize.

in 10.10 netbook, that unity is not customizable, if i remember right, compiz is not even installed since mutter is used for the ui.
natty(11.04) has the compiz version of unity, but it is still very much work in progress.

---

### Post by darronwolflx on 2011-02-25
I've also encountered this same problem and have been searching for a solution. I was completely clueless but now will start working on the codes and suggestions. Thanks for in advance for all the help!

---

