---
title: "GNUsTicker (http://gnusticker.sourceforge.net/)"
date: 2006-06-20
forum: Desktop Environments
---

### Post by jrattner on 2006-06-20
Like several others (based on a search of this forum) I have tried to install GNUsTicker and failed.  GNUsTicker is the equivalent of Knewsticker for KDE.  I followed the directions and compiled it from source.  I believe the problem lies in the fact that its a bonobo component.  So I installed everything bonobo from synaptic and did a killall gnome-panel and still have not got it to work.

After installing from source GNUsTicker appears in the "Add To Panel" screen in gnome, but when I choose to add it to the panel NOTHING happens.  Please someone offer some incite.

Here is a link to the website: 
[http://gnusticker.sourceforge.net/]("http://gnusticker.sourceforge.net/")

Here are the installation instructions and note from the website:

> nstalling instructions
for common installation...

./configure --prefix=/usr
make
sudo make install

After installation you must add the applet by the "Add to Panel..." GNOME panel menu. 

> NOTES
Since it is a bonobo component, you must ensure that the .server file it is installed on a path reacheable by bonobo activation server. (for example: for Fedora distribuition, the installation path should be set as follow: ./configure --prefix=/usr ). Otherwise you must properly set the BONOBO_ACTIVATION_PATH to [your choosen prefix]/lib/bonobo/servers in you ~/.bash_profile file 

---

### Post by lcohen999 on 2007-07-27
Thought I would bump this as I would love GNUsTicker working

---

### Post by nightcrawler27 on 2007-12-21
I got it to work. I found two problems. Also note that I do not run ubuntu, I run Debian.

First, a few things:

It appears you were at least able to compile the code and get the .server file into the bonobo servers path on your system, or you wouldn't have gotten this far. So it sounds like you have all the dependencies, etc. One you may not have is the python-xml package...during my troubleshooting, I discovered I did not have this adn GNUsTicker relies on the "xml.marshal.generic" package. Before you go any further, check to see if you have python-xml installed. (maybe ubuntu automatically provides this) If not, issue the following:

"apt-get install python-xml"

Next problem is in the code itself. I discovered that the "gnusapplet.py" code attempts to import "gnome.applet". In more recent versions of the gnome development packages, gnome.applet has been depricated. The proper name is "gnomeapplet" (without the . between 'gnome' and 'applet'). There are several calls to gnome.appplet in the code. I modified the code to reflect the newer applet name, and I stopped getting the error. It runs fine on my system.

I have also submitted my modified code to the developer of GNUsTicker. You should find the gnusapplet.py file in /usr/libexec/GNUsTicker if your install went correctly.

---

### Post by alamarco on 2008-01-26
I know this post is over a month, but wondering if anyone has any other information on GNUsTicker? I'm in the same boat and I have python-xml installed and modified my gnusapplet.py.

One thing I noticed is that in my home directory when I try to add the applet GNUsTicker creates the following directory tree: "GNUsTicker/apps/panel/applets/applet_12/prefs/". However it's empty :(.

Is there anything else to edit? Possibly could you attach your file?

---

### Post by aaronfulton on 2008-01-26
I am attempting to install the GNUsTicker right now and alot of the python dependendcies are not part of the standard Ubuntu installation and need to be downloaded. If your having problems with the installation try running : 
./configure --prefix=/usr
and then check to see were the error occurs and then use Synaptic to find the dependecy.

i.e. i received this error:
configure: error: could not find Boost python headers look at [http://www.boost.org](http://www.boost.org)

And used synaptic to download:
libboost-python 1.34.1-2
libbost-dev
 
And this corrected this ONE error but trust me there are a few dependencies conflicts you will have to sort through and resolve but it will work.:)

If you still have problems I am more than happy to help you work through them

---

### Post by alamarco on 2008-01-26
The problem I'm having is adding GNUsTicker to the panel. I installed all the dependencies and GNUsTicker compiled successfully. After moving the gnome-GNUsTicker.server file to correct directory, the GNUsTicker applet shows up in the Add To Panel dialog window. When trying to add to the panel nothing happens except directories being created in my home folder.

nightcrawler27 indicted that you had to change the gnusapplet.py file. I backed up the file, changed the indicated lines and it still can't launch. The thing that makes it worse is because GNUsTicker is run from the command line I don't know of anyway to generate an error message to see what could possibly be wrong.

If it helps I've compiled using the ./configure --prefix=/usr command and moved GNOME_GNUsTicker.server file from the python directory of the source tarball to the /usr/lib/bonobo/servers/ directory.

Thanks

---

### Post by nightcrawler27 on 2008-04-02
> **alamarco said:**
> The problem I'm having is adding GNUsTicker to the panel. I installed all the dependencies and GNUsTicker compiled successfully. After moving the gnome-GNUsTicker.server file to correct directory, the GNUsTicker applet shows up in the Add To Panel dialog window. When trying to add to the panel nothing happens except directories being created in my home folder.

nightcrawler27 indicted that you had to change the gnusapplet.py file. I backed up the file, changed the indicated lines and it still can't launch. The thing that makes it worse is because GNUsTicker is run from the command line I don't know of anyway to generate an error message to see what could possibly be wrong.

If it helps I've compiled using the ./configure --prefix=/usr command and moved GNOME_GNUsTicker.server file from the python directory of the source tarball to the /usr/lib/bonobo/servers/ directory.

Thanks

Wow I haven't checked this thread in months, I figured it was dead...I stopped using GNUSticker as I was noticing other bugs that made life difficult. But it seems enough people are interested that I may see if I can resolve some of these other issues. Since my last post I have gotten no feedback from the developers of GNUSticker....I may make an attempt at forking it and getting it to work right. I will fire it up again and see what I can do.


nightcrawler27

---

### Post by lcohen999 on 2008-04-02
Please do!

The only thing I am missing with my GNome setup is a scrolling news ticker.

Let me know if you need some help testing...and thanks!

---

### Post by nightcrawler27 on 2008-04-03
Ok I just turned GNUsTicker back on and it seems to be working. So here is as much details as I can provide about my setup. Again, note that I am not running ubuntu, I am running debian etch, which is just about the same thing. I will attempt to run it on an actual ubuntu install soon.

So what I did:

Installed GNUsTicker as per instructions. Besides any dependencies that GNUsTicker may require, my system is running the following that may be important to know:

Debian Etch (Debian-2.0.0.12-0etch1) on i686
Gnome 2.14.3
gtk/libgtk2.8.20-7
python 2.4.4-3
python-gnone2 2.12.4.6
python-gtk2 2.8.6-8
gcc 4.1.2 20061115

After installation: I have the following files/dirs on my system:
/home/<username>/GNUsTicker/apps
/home/<username>/GNUsTicker/main
/usr/share/GNUsTicker
/usr/share/GNUsTicker/images
/usr/libexec/GNUsTicker (this is where the main program actually gets installed).

I have the bonobo server file for GNUsTIcker in the following location:

/usr/lib/bonobo/servers

the name of the file is GNOME_GNUsTicker.server and has the following properties:

-rw-r--r-- 1 root root   1287 2007-12-21 13:19 GNOME_GNUsTicker.server

after install I did the modifications as I mentioned earlier to the gnusapplet.py script.

Then I right-clicked the gnome task bar, left clicked "Add To Panel" and the GNUsTicker item is there. I added it to the panel with no issues.

Hope this helps

Nightcrawler27

---

### Post by nightcrawler27 on 2008-04-03
All,

Another update on the GNUsTicker issue...I am now running Ubuntu 7.10 Gutsy. I am either pleased or disappointed to say that my code changes in fact did nothing and I am running GNUsTicker without any modifications to the code. GNUsTicker still leaves much to be desired, but it does work "out of the box".


Here are my stats:

Ubuntu 7.10 (Gutsy) kernel 2.6.22-14-generic
Gnome 2.20.1

I updated everything to the latest updates, but the following packages seem pretty significant: binutils bison build-essential (this is a big one!) g++ gcc gtk2 libboost-dev libboost-python libboost-python-dev libgtk python python-dev.

Is there enough desire for this program in GNOME? If so I would still take a shot at forking it and maybe Canonical would want to include it in the distro or repositories?

nightcrawler27

---

### Post by nightcrawler27 on 2008-04-07
All,

After reviewing the code for GNUsTicker, I say screw forking this, I'm writing a new one from scratch. There is a much easier way to do this, and I have so many other ideas I'd much rather start from the ground up then try to integrate my thoughts into this code. When I have a name and and code that I can release in alpha status, I will let you guys know if anyone is interested in testing.

nightcrawler27

---

### Post by lcohen999 on 2008-04-07
Running 8.04 beta, you know I'm ready for testing when you are

Thanks!

---

### Post by Mr Mark on 2008-04-18
I've been searching for a panel-based ticker since starting with Ubuntu.  I even tried Kubuntu for this very reason but found I preferred Gnome for whatever reason.  Anyways, I look forward to giving your attempt a test-drive nc27.

In the meantime, is [SashXB]("http://www.cs.berkeley.edu/~aj/cs/sashxb/library/tour/") likely to be of any use to me?  I'm at work on my Windows lappy so no chance of giving it a spin so I wondered if anyone else had used it?  I've only given it a cursory glance-over but there's a "Newsbar" applet ("weblications", they call them) that resides in the Gnome panel and looked quite promising.  Anybody know if it's any cop?

[eta]  I did a search for "SashXB" on the forums and drew a blank.

---

### Post by nightcrawler27 on 2008-04-18
> **Mr Mark said:**
> I've been searching for a panel-based ticker since starting with Ubuntu.  I even tried Kubuntu for this very reason but found I preferred Gnome for whatever reason.  Anyways, I look forward to giving your attempt a test-drive nc27.

In the meantime, is [SashXB]("http://www.cs.berkeley.edu/~aj/cs/sashxb/library/tour/") likely to be of any use to me?  I'm at work on my Windows lappy so no chance of giving it a spin so I wondered if anyone else had used it?  I've only given it a cursory glance-over but there's a "Newsbar" applet ("weblications", they call them) that resides in the Gnome panel and looked quite promising.  Anybody know if it's any cop?

[eta]  I did a search for "SashXB" on the forums and drew a blank.

I have not used this, but the thing about "code generators" such as this typically include lots of code that is unnecessary. 

From the page [http://developer.gnome.org/feature/archive/sashxb/:](http://developer.gnome.org/feature/archive/sashxb/:)

First, what SashXB is:

a way to embed Mozilla in various places on the desktop, and extend JS with access to native APIs. Combined with a friendly and powerful development environment, it allows you to build full-featured desktop applications ("weblications", sorry, we didn't invent the term) built around HTML and JS. 

From Linux.com: 

SashXB uses Mozilla's HTML layout engine, JavaScript interpreter, and Component Model, and it uses several components from the GNOME project. According to IBM, SashXB extends the Gnome desktop with Mozilla in the same way IE does for MS windows. SashXB creaes a new-hybrid Web development model for Linux, and it could also work with KDE in the same way.

None of this sounds like something I would want as part of an RSS reader, or anything else for that matter. Many people hate MS and IE because of its extension and integration into the desktop and Windows. Likewise, I don't see Linux users seeing this kind of browser-desktop-OS integration as a positive thing. Why can't a browser just be a browser rather than an "extension of my desktop"?

Anyways, I am making progress and hopefully will have something significant to report in the coming weeks. My goals are to have something that is fast, simple, native to GNOME, and to not require a bunch of dependencies that a typical user might not otherwise already have on their system. It should also be brain-dead easy to install. After all, who wants to jump through hoops of fire for an RSS reader?

nightcrawler27

---

### Post by hidinginthemountains on 2008-04-24
I've just been suffering through trying to get this running myself. I know I would appreciate a fresh attempt at what I think would be a great little addition. I've been wanting a little panel app like this since I installed the first time. If I was a developer, I would've tried one myself.

If you do take a shot at this, let me know. I'll test.

---

### Post by nightcrawler27 on 2008-04-25
I am definately taking a shot at this. I just registered my project at SourceForge and am awaiting approval. When I have something significant for people to try I will post some sort of a package there and provide a link to the project.

nightcrawler27

---

### Post by nightcrawler27 on 2008-05-05
Ok just figured I'd give an update...I have been able to do the following:

[LIST]
[*]create a ticker
[*]put the ticker in the GNOME panel
[*]parse news items from a locally stored xml file
[*]display the items in the ticker
[/LIST]

For some reason the damn thing crashes about 50% of the time since I added the code for parsing the XML, so before I do anything else I need to sort that out. I still have quite a ways to go. But I have a project on sourceforge, although I have not posted any code yet. When I can get the thing to stop crashing, and I have some sort of a README that lists system requirements and how to install, I will post what I consider an alpha version. The name of the project/application will be newScroller. (For now anyway, not quite settled on the name, apparently there used to be an app out there called "@1 Newscroller" but is quite different from what I am doing.)


Nightcrawler27

---

### Post by deli.ds on 2008-05-17
I have been trying to get GNUsTicker to work with Gutsy until I found this thread. Also interested in testing your app Nightcrawler27. Keep us updated!

---

### Post by nightcrawler27 on 2008-06-12
Just to bump this thread, I am still working on this...I haven't had much to report. I have been working with several different methods of rendering the news feeds, however I have hit roadblocks with each one. I am not much of a developer, so even getting this far has been a huge learning curve. I will keep plugging away at this though, and you will all know when I have something worth showing.

Nightcrawler27

---

### Post by Mr Mark on 2008-06-13
Thanks for the update.  I check this thead a lest twice a wee to see if there's anything new.  Good luck with the work boss! :)

---

### Post by king76 on 2008-06-27
Hi,

Me too, I want new version of GNUsticker !

Please ;)

Thks

---

