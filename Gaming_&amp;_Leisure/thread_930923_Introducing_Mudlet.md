---
title: "Introducing Mudlet"
date: 2008-09-26
forum: Gaming &amp; Leisure
---

### Post by Vadi on 2008-09-26
[size="4"]Hi![/size]

I'd like to announce a new mud client, [[img]http://mudlet.org/favicon.png[/img]Mudlet]("http://mudlet.org/"). It's being made from scratch, designed to be **fast**, **easy to use**, and easy to **script** with - while also offering some very powerful **features**. In short, the best of all clients without the bugginess or complexities wink.gif (and we know what we're doing, too!)

The client will also feature some really nice things not found in existing clients - like [Mud Styles]("http://mudlet.org/63/mud-styles-update/"), advanced scripting support (linear and multi-threaded approaches, along with support for many scripting languages such as Lua, Python, Perl, Ruby), built-in app store, and other nice stuff.

More information is available here ([http://mudlet.org/about/]("http://mudlet.org/about/")).

[size="4"]Beta testing[/size]

The client isn't out yet, but you're welcome to sign up for the beta test notifications here ([http://mudlet.org/download/]("http://mudlet.org/download/")). The beta will be open - so anyone who'd like to give it a try will be welcome to.

[size="4"]Ideas[/size]

Have an idea you'd like to see implemented in the client? Yours thoughts are welcome. Feel free to post all your stuff here: [http://forums.mudlet.org/forum/fresh-ideas]("http://forums.mudlet.org/forum/fresh-ideas"). We have many of our own, but new input is always useful.

[size="4"]Windows? Linux? Mac?[/size]

The client will definitely run natively on Windows and Linux. Macs - chances are looking good too, but no guarantees.

[size="4"]Cost?[/size]

Zero, zilch, nada. The client is [free software]("http://www.gnu.org/philosophy/free-sw.html") and [open source]("http://www.opensource.org/docs/osd"). Really! That also means you're welcome to contribute to making it better smile.gif
[size="4"]
Technical stuff[/size]

The client is coded in C++, using Qt 4 as the gui toolkit. Lua, Python, Perl and Ruby will be the supported scripting languages at first - and more will be added as they're needed.

[size="4"]Forums[/size]

We got forums over here ([http://forums.mudlet.org/]("http://forums.mudlet.org/")), feel free to post stuff.


Comments? Questions? :)

---

### Post by Vadi on 2008-11-08
See [http://mudlet.org/134/mudlet-pre-alpha/](http://mudlet.org/134/mudlet-pre-alpha/). Beta was delayed, but a pre-alpha started - if you have good lua experience, please give this a try!

Sneak peek at what you can do: input manipulation. Heiko made this small sample script...

regex: say.*(\w+).*(\w*).*(.*)
script: sendRaw( "say " .. matches[3] .." " .. matches[1] .." ".. matches[2] )

result:
[img]http://www.ubuntu-pics.de/bild/5401/screenshot_02_W81vdU.png[/img]

And other interesting stuff. If you know Lua well, please join in the testing :).

---

### Post by Greslore on 2008-11-08
Nice!  Definitely keep us updated to the status of this.  I have yet to find a good client I really like that works on Linux.  This one sounds very promising.

---

### Post by Vadi on 2009-01-24
A PPA is now available: [https://launchpad.net/~mudlet-makers/+archive](https://launchpad.net/~mudlet-makers/+archive)

---

### Post by chaosprime on 2009-01-25
Kudos.  Added you to my MUD's web resources / clients list page immediately. :)

---

### Post by binbash on 2009-01-25
> **Vadi said:**
> A PPA is now available: [https://launchpad.net/~mudlet-makers/+archive](https://launchpad.net/~mudlet-makers/+archive)

thanks for ppa

---

### Post by Vadi on 2009-01-25
Just a note though - we're currently in a rather [alpha]("http://www.mudlet.org/download/") stage, so the quality polish isn't fully finished :)

---

### Post by Metaljaz on 2009-01-25
This is way interesting. I have been jumping mudclients because no particular one has all that i need. Please keep us posted on this project.

---

### Post by fugazi32 on 2009-01-27
Looks interesting, I usually use my plain old *telnet* client, but this looks cool.

---

### Post by Vadi on 2009-01-29
A PPA is now up: [http://www.mudlet.org/download/](http://www.mudlet.org/download/)

---

### Post by Deeta on 2009-02-21
could it be that the current mudlet version disappeared from the repo?
(noticed some days ago that it was listed as local package in synaptic and as it still is i guess it is not some quirk of apt)

---

### Post by Vadi on 2009-02-21
It had a bug that when connecting, would eat up all your ram/swap. There will be a beta soon, and it'll be back in the PPA.

---

### Post by trendyabinash on 2009-02-22
Sir what is this Mudlet???

It sounds interesting can I have an idea about what it does??

---

### Post by Vadi on 2009-02-22
See [http://www.mudlet.org/about](http://www.mudlet.org/about)

---

### Post by capennington on 2009-04-03
Hey, i'm looking for a good client also.  Tho i'm a newbie at ubuntu so I don't know how to change my software sources list :(.

Is there a link to just download the .deb file or anything?  Just curious

Thanks,
Cap

---

### Post by Vadi on 2009-04-03
There is a .deb, but then you won't be auto-notified of updates if you don't add the repository.

Here are good instructions: [https://help.ubuntu.com/8.10/add-applications/C/extra-repositories.html#extra-repositories-adding](https://help.ubuntu.com/8.10/add-applications/C/extra-repositories.html#extra-repositories-adding)

---

### Post by gwydionwaters on 2009-10-26
i have an issue, i added the repository but when i try to install it says dependencies can not be met but there are none in the dependencies tab for the package nor the details of the error. also i can't import a txt file pgp key, it has to be a pgp file. this is in karmic using kde 4.3. looks great though, just wish i could try it out :)

---

### Post by Vadi on 2009-10-26
I'm working on making it Karmic-friendly.

---

### Post by gwydionwaters on 2009-10-26
ok, thank you :D

---

### Post by Vadi on 2009-10-26
I've fixed it.

---

### Post by gwydionwaters on 2009-10-26
it doesn't appear so over here, still get an error about inability to satisfy dependencies.

---

### Post by Vadi on 2009-10-26
reload your repository sources

go to synaptic and click 'reload'

---

### Post by gwydionwaters on 2009-10-26
there must be something wrong with the package, i have updated the list a few times. i still get the error. i do not, however, use synaptic. i use kpackagekit, which works quite flawlessly otherwise so i don't think it is an error there. let me try apt in a moment, i'll let you know

```

rob@ubox009:~$ sudo apt-get install mudlet
[sudo] password for rob:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  mudlet: Depends: libqscintilla2-3 (>= 2.3.2) but it is not installable
E: Broken packages

```according to apt libqscintilla2-5 replaces this, i will try that and come back
.. hmm, already have that version installed

---

### Post by Vadi on 2009-10-27
Well, your repository sources still are not refreshed. The error you showed to me is no use because that is what I fixed. You need you refresh your list, "sudo apt-get update"

> vadi@vadi-laptop:~/Programs/Mudlet2$ apt-cache policy mudlet
mudlet:
  Installed: 0.2~beta15~ppa4
  Candidate: 0.2~beta15~ppa4
  Version table:
 *** 0.2~beta15~ppa4 0
        500 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
        100 /var/lib/dpkg/status
vadi@vadi-laptop:~/Programs/Mudlet2$ 


---

### Post by sthrnpagan on 2010-03-02
I love this mud client. so much bettter than others i have tried for Linux. Kudos to you.

---

### Post by EmilyRose on 2010-03-09
Ok, so I just downloaded mudlet, and my first impression is that I'm impressed;) I like it! It reminds me of my beloved zmud :sniffle:

---

### Post by EmilyRose on 2010-03-13
So, after using mudlet for a few days, I'm still impressed, but the one feature that I miss from zmud/mushclient is autowalk/speedwalk I've got mudlet setup using alias' for it, but its just a slightly more cumbersome way to do so... So, add speedwalk/autowalk an it'l be perfect;)

---

### Post by Vadi on 2010-03-14
The following function is included with mudlet: [http://forums.mudlet.org/viewtopic.php?f=6&t=1168&p=2366&hilit=speedwalk#p2366](http://forums.mudlet.org/viewtopic.php?f=6&t=1168&p=2366&hilit=speedwalk#p2366)

---

### Post by sthrnpagan on 2010-04-19
I am a happy user of Mudlet to play Medievia. Mudlet is great. However, unlike mm2k6 there is no secondary window for chat (i.e. clantalk, formtalk,etc.) I would love for that feature to be a part of Mudlet, as when Im running for xp or a trade run i miss what ppl are saying as we move very fast.

I have tried to use the tab-window-chat pkg on the Mudlet website but Have no idea how to use as there are not detailed instructions on how to use.

---

### Post by Vadi on 2010-04-19
It's up to the users to make the chat window - all the functions are there. The tabbed chat window is one of them, but requires some coding to make it work for your MUD (so the triggers match on the channels properly and etc)

---

