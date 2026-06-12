---
title: "Installing Themes on Ubuntu, GTK+ Engine Error"
date: 2009-01-01
forum: General Help
---

### Post by jdwashere on 2009-01-01
Well I'm still very new to Ubuntu and I'm trying to install new themes.

I'm currently trying to install the Elegant Brit theme. When I go to set this as my theme it gives me the error GTK+ Engine not installed so it doesn't look correct. 

I've searched and searched all day looking for an easy to understand tutorial on how to install an engine. So far I've  only been    able to successfully installed 1 theme and that was just by typing in one command into terminal. I've only been  able to install 1 engine and it was a .deb file so it was simple enough.

I  don't know what   to install, let alone how. So any help would be dramatically appreciated. 

Thanks.

---

### Post by PierreDeKat on 2009-01-01
First, it might help if we knew what version of Ubuntu you're running. Hardy? Intrepid?

And are you using Gnome? KDE? XFCE? 

GTK is a Gnome deal, and I have a hunch it's not installed, by default, on Kubuntu or Xubuntu.

Second, depending on where you're getting your themes, I wouldn't hold my breath trying to get a particular theme to function the way that the person who built it purports to have gotten it to work.

There are a lot of artsy fartsy types making themes and/or skins, but only about a quarter of them bother to test, fix bugs, or otherwise support the themes/skins they've supposedly created.

I guess that's the thing about artsy fartsy types.

I love what they do when they do it right. But I've also had some themes/skins crash me in a real bad way.

---

### Post by jdwashere on 2009-01-01
The Ubuntu version I'm using is 8.10.

The theme, along with others I've been trying is from gnome-look.org.


Link to theme I'm trying to get working: [http://www.gnome-look.org/content/show.php/Elegant+Brit?content=74553](http://www.gnome-look.org/content/show.php/Elegant+Brit?content=74553)


I'm still very new at Linux/Ubuntu and I am confused on installing most things. Again any help on telling me what to look for or a more in depth tutorial would be very much appreciated.

---

### Post by PierreDeKat on 2009-01-01
Okay, well, one of the handiest things about Ubuntu is that, if you go to System->Administration->Synaptic Package Manager, you can see around 20,000 different packages/applications that you can install by simply ticking them off and clicking "Apply".

And if you installed regular Ubuntu (which comes with the Gnome desktop), you can search for "gtk2-engines", and you should find that it's already installed by default.

So I thought I would check out this theme to see what happened, for myself, and it will install, though it does pitch up a warning about gtk2-engines. My guess is there's some sort of bug somewhere.

But like I said, it does install. If you go to System->Preferences->Appearances, go to the "Theme" tab, click the "Install" button, navigate to the downloaded theme -- download the one that says "GTK & Metacity themes" -- it should install.

Once you get it installed, you will probably want to play around with the "Customize" button to change some more colors to "black", change icons, and so on.

---

