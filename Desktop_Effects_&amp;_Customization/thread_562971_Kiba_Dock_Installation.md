---
title: "Kiba Dock Installation"
date: 2007-09-29
forum: Desktop Effects &amp; Customization
---

### Post by mlyons16 on 2007-09-29
I recently came accross this blog post at: [URL="http://fusioncast.blogspot.com"]http://fusioncast.blogspot.com
[/URL]
> So, I've been very busy at school, but since people have asked, here is a short howto for Kiba-Dock. I hear the AWN instructions are easier to find...

First, install Subversion to download the source code:

sudo apt-get install subversion

Then visit this page, and install the dependencies (using Synaptic Package Manager, and including the names with -dev).

run:

svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/) kiba

and then:

ls

and then take a look at the list. There should be about five blue items. You'll want to go into each of these with the cd command:

cd akamaru

for example. After you cd into it, run:

./autogen.sh
make
sudo make install

and then when those commands are done, run:

cd ../insert_next_directory_name_here

and do the three commands again.

Once all of that is finished, you should be able to launch kiba-dock from your menu. Good luck!

I'm just a little confused as to how they match up to Kiba Dock's installation wiki:

>  Building dependencies

The source code for Kiba is in a SVN repo, so you will obviously have to install subversion

Here are some generic dependencies you will need in order to build Kiba (and nearly every C project around here):

    * intltool
    * libtool
    * automake
    * autoconf
    * gcc
    * gettext

Here are some dependencies needed in order to build the kiba-dock part of Kiba:

    * gtk+ >= 2.8.0
    * cairo >= 1.0.0
    * libxml-2.0
    * pango >= 1.10.0
    * Optional: librsvg > 2.14.4
    * Optional: glitz >= 0.5.3
    * Optional: akamaru

Below is the list of some dependencies you will be asked for when building the kiba-plugins part of Kiba:

    * libgnomevfs > 2.0.0 is required by the trash plugin and the stack plugin
    * libgtop > 2.0.0 is required by the sysinfo plugin
    * dbus is required by the dbus plugin
    * libgnome-menu is required by the gmenu plugin
    * libgnomeui-2.0 > 2.0.0 is required by the stack plugin

Finally, building the kiba-dbus-plugins part of Kiba will require the following dependencies:

    * pygtk2-devel

and 

> Treviño manages a repo with kiba-dock, These can be accessed by adding the following to your sources.list file: Note: Currently, there are only 32 bit (x86) deb packages available, 64 bit users can use SVN.

   1. Configure your system to be using Treviño's repository by adding the following to lines in your /etc/apt/sources.list file:
          * If you are using Edgy Eft (6.10):
                o deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
                o deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn
          * If you are using Feisty (7.04):
                o deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
                o deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
   2. Import Trevino's GPG key:
      $ wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -
   3. $ sudo apt-get update
   4. $ sudo apt-get install kiba-dock
   5. $ sudo apt-get install kiba-dock-dev
   6. $ sudo apt-get install kiba-plugins

PLEASE NOTE: this is a daily svn repo, which means you're dealing with snapshots of the latest and greatest, but not always the most stable!

---

### Post by kakalaky on 2007-09-29
The easiest way to get kiba-cock would be with this part of your post:
> 
1. Configure your system to be using Treviño's repository by adding the following to lines in your /etc/apt/sources.list file:
* If you are using Feisty (7.04):
o deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
o deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
2. Import Trevino's GPG key:
$ wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -
3. $ sudo apt-get update
4. $ sudo apt-get install kiba-dock
5. $ sudo apt-get install kiba-dock-dev
6. $ sudo apt-get install kiba-plugins

---

### Post by mlyons16 on 2007-09-29
Now can I just add the:

deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

in Synaptic Package Manager, or do I need to open terminal. Or can the two methods be used interchangeably? Futhermore, what is the deal with installing suberversion? I should do that before I add the repos in Synaptic correct?

Lastly, those "dependencies" listed all in the 2nd quote of post 1 are just like packages i need to make sure i mark for installation in Synaptic? Is that correct?

Okay, besides all of the above questions. I have one more question. Is Kiba Dock superior to Avant Window Manager's dock? I want to be using a dock that will especially give me stacks. I really like that feature in Mac OS X Leopard but I don't want to use Mac.

---

### Post by kakalaky on 2007-09-29
Synaptics just changes your sources.list so you can use it interchangeably.  I don't know if synaptics will let you import the key so you might still need to run the following in a terminal:
```
wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
```

After that just update your package list from synaptic or with:
```
sudo apt-get update
```

Then you can just kiba-dock, kiba-dock-dev and  kiba-plugins from synaptics or use this:

```
sudo apt-get install kiba-dock
sudo apt-get install kiba-dock-dev
sudo apt-get install kiba-plugins
```

All the needed dependencies will be installed automatically.

---

### Post by mlyons16 on 2007-09-29
alright excellent. I'm presently in 7.10 beta on the live cd, so i'm gonna give that  a try. I love the quality of the free support here.

---

### Post by kakalaky on 2007-09-29
Well, the packages are for feisty so I can't guarantee they will work on gutsy.  I don't see any reason why they wouldn't though.  The repo will cause conflicts with the compiz-fusion already on gutsy though.

---

### Post by mlyons16 on 2007-09-30
Ya, my main distro is 7.04 Ubuntu right now. 7.10 is too buggy right now for my liking.

I thiiiiiiiink I got it working, that installation.

Can some one like tell me what the steps are in a 1., 2., 3., ... layout. I sort of know what I have to do from Kiba's wiki, but I'm a little bit lost yet.

I'd really appreciate it. I'll probably be able to figure out customisation later, but I want to ensure I have a proper install first.

Thanks in advance.

---

### Post by anemptygun on 2007-09-30
The way I installed kiba-dock, and the easiest way I think is using trevino's repositories.

---

### Post by mlyons16 on 2007-09-30
yes, i know to use the repositories. I just add them in synaptic right?

Whats this about installing some key, and installing subversion?

I installed subversion thru terminal b4 i added the repos in synaptic.. but i never installed a key.. i got a little confused there. Can some one give me ALL THE STEPS listed in order of execution on Feisty Fawn??

---

### Post by anemptygun on 2007-09-30
Ok, so i don't know of anything anything about subversion. But this is what I did to get kiba-dock working. I am assuming you already have the restricted drivers installed.

First I enabled the repositories. Go to System -> Administration -> Software Sources, click on the second tab (Third-Party Software), then click on the ;Add" button and paste the following code:

```

deb http://download.tuxfamily.org/3v1deb feisty eyecandy

```

```

deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy

```

Leave the sources window open and type in the terminal:

```

wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg

```

```

sudo apt-key add DD800CD9.gpg

```

Now click the "Close" button on the Software Sources window and you will be asked if you want to reload the information about available software, so click the "Reload" button and wait for the window to disappear.

Type the following lines in the terminal window:

```

sudo apt-get update

sudo apt-get -y upgrade

```

Then just type in the terminal:

```

sudo apt-get install kiba-dock
sudo apt-get install kiba-dock-dev
sudo apt-get install kiba-plugins

```

---

### Post by mlyons16 on 2007-09-30
very good. That's what I wanted to know from Day One. 

You should contribute that to the Kiba Wiki:

[http://www.kiba-dock.org/](http://www.kiba-dock.org/)

The link for the Wiki is on the left side of the page.

---

### Post by santiagoward2000 on 2007-09-30
> **anemptygun said:**
> The way I installed kiba-dock, and the easiest way I think is using trevino's repositories.

Agreed. I also intalled it from Treviños repositories :lolflag:

---

### Post by anemptygun on 2007-09-30
No problem. What I do know about I try to share. Thanks :)

---

### Post by mlyons16 on 2007-10-19
are these instructions generally applicable to 7.10 now?

---

### Post by anemptygun on 2007-10-19
good question, i haven't tried yet...

---

