---
title: "Help me, I am new to K"
date: 2009-05-02
forum: General Help
---

### Post by MIH1406 on 2009-05-02
Hi,

I am a Ubuntu user but not Kubuntu user and want to learn how to use kubuntu. I faced many problems:
1- Where is Synaptic?
2- Where is Add/Remove Applications (With popularity sorting and applications names not packages name!!)
3- Where is the (System Update).

All these are very easy with gnome.

Thanks,
Mohammad

---

### Post by davetv on 2009-05-03
Synaptic is not installed by default but can be added through "adept". Adept also handles system updates.

---

### Post by rdmike on 2009-05-03
I'm new to Kubuntu too, though familiar with Ubuntu. That said, it looks like the "K" version does away with a simplified package handler opting instead for a more spartan and, in my opinion, less user-friendly approach. 

From the way it looks to me you'll need to install synaptic yourself if you want to use that option. For non command line installation of software click the "Kickoff Application Launcher" (The big blue "K" in the lower left portion of your screen), then click the "Applications" tab, then, from the list, click on "System", and finally click on on "Software Management."

Once in this window you'll need to type in the name of the application you wish to install or a relevant term to perform a search e.g. Kubuntu Restricted Extras or Gstreamer for a more generic type of result.

Now, once you've done that you have to click on the specific package/application you wish to install and click "apply." --Note: I found it a bit confusing to tell, at first, whether I already had a specific package installed or was adding/deleting one because of the +/- control scheme employed. However, it gets easier once you figure out that if you have a little brown folder showing, when looking at a particular application or package that means it's currently installed.--

Of course you can still use the terminal to manually install an application using the "sudo apt-get" command if you prefer.

There may be a better way of doing this but, if so, I don't know what it is lol.

To me it's a very strange and convoluted means of getting from point "A" to point "B." On the other hand, I've found Kubuntu to be clean, fast, and otherwise quite good so far. I especially like how much simpler it is, to me, to tweak desktop effects; much less hassle than straight Ubuntu. 

So, assuming you've read this far it's a little of the proverbial give and take. Hopefully the development team will tweak package handling soon.

Hope that helps. :)

---

### Post by Aries K on 2009-05-03
Ok, first things first:

1. You do not need to download any package manager. You already have KPackagekit out the gate.

2. Adept is dead, Kpackagekit is the replacement for it.

3. Kubuntu did not get rid of a simple package manager for a difficult one. It has it's own easy to use package manager where you can add/remove software, system update, and edit software sources all in one place. Kpackage kit is as simple as simple is going to get.

To access Kpackagekit go to System Settings>Add and Remove Software. From there you should already be at Software Management and be able to add/remove software. Kpackagekit's interface is simple and not cluttured at all. You should get the hang of it pretty quick. Enjoy. :)

---

### Post by rdmike on 2009-05-03
That's the exact same thing as going to "software management"; not nearly as "simple" as what's featured in Gnome. For example, nothing is listed for a user to browse through as in Gnome. You either have to guess at a good search parameter or know the name of what you're after.

Now, if there's something I'm missing please pass the info along as I'd love a less cumbersome approach.

---

### Post by agim on 2009-05-03
I love kubuntu, but for me, nothing compares with synaptic, so I use synaptic with kubuntu. Its better integrated in kde 4.2, even if its just a little ugly compared to the rest of my shiny kde desktop.
You can also use the terminal with apt-get or aptitude as well, if you want to know what synaptic is doing behind the scenes. Its not as hard as you think.
Can't beat the synaptic feature that allows you to browse apps though, which is why I use it, as well as the terminal.
I let kpackagekit handle my updates. (Or just run the following).

sudo apt-get update && sudo apt-get upgrade

---

### Post by rdmike on 2009-05-03
Do we need to install synaptic or is it pre-installed? I've used it before.

Thanks for the info btw, hope my reply didn't sound pissy lol.

---

### Post by agim on 2009-05-03
I install synaptic. It will be a big download, because it has to download some other gnome stuff. But if you plan on using ANY gnome software, you will have to do this anyway.
On a personal level, I have always thought it ridiculous to limit oneself to only gnome or kde. I have both installed at any given time (along with openbox or fluxbox or lxde or xfce whatever else catches my eye at any given moment). I prefer kde since kde 4.2 came out, so when I can I go with kde apps, but when something is much better, like synaptic, I see no reason not to use it.

---

### Post by MIH1406 on 2009-05-03
Thanks guys
it is really simple I just did not know that the plug icon is the network manager!! so I could not have a connection and every thing couldnot work without it. But now I installed every thing I need.

Thank you all.

---

### Post by MIH1406 on 2009-05-03
KPakageKit is an alternative to Synaptic no problem with this. But Is there and alternative to the (Add/Remove Applications)?

It orgnizes installing applications very well.

Thanks,
Mohammad

---

### Post by Aries K on 2009-05-03
> **MIH1406 said:**
> KPakageKit is an alternative to Synaptic no problem with this. But Is there and alternative to the (Add/Remove Applications)?

It orgnizes installing applications very well.

Thanks,
Mohammad

While in KPackagekit go to Software Management. At the last drop-down (on the right hand side) where it says "All Packages". Choose whatever category of software you are looking to install. For example choosing "KDE" will list what KDE apps you have installed and what KDE apps are available or clicking "Games" will show what games you have installed or what games are available. NOTE: Again this will also show software that  is already installed as well. To install software click the green + symbol on the side. If the software is already is installed it will show a - symbol and you would click the - to uninstall software. So yes you can browse through apps in KPackagekit. It is different than Synaptic but is it harder to use? Not really it is just a matter of preference. Once you get the hang of it you won't have to worry about installing Synaptic and all of the Gnome dependencies that come with it. Anyways good luck and enjoy.

---

### Post by MIH1406 on 2009-05-05
But you cannot limit your search within a category and the packages names are not clear, it uses the package name instead of the application only as in the Add/Remove apps in gnome. Also you do not have the popularty contest result for the applications.

Thanks

---

