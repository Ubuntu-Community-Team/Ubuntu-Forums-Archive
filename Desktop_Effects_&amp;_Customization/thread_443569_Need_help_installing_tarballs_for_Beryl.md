---
title: "Need help installing tarballs for Beryl"
date: 2007-05-14
forum: Desktop Effects &amp; Customization
---

### Post by TheThinker on 2007-05-14
Hi again fellow Linux users! The help I've been getting has been excellent by the way, and you all have my gratitude! Since I'm a noob, I want to install Beryl on my Ubuntu Feisty Fawn but I haven't a clue on how to install the tarballs I downloaded from the Beryl Project website. I downloaded all of the tarballs for their latest version, and the computer in-question does NOT have internet access yet, so any offline guides on how to install tarballs is greatly appreciated. 

Before I forget, my computer is a Celeron 2.8ghz processor with an Nvidia MX4 4000 graphics card. The graphics card is already fully enabled with its proper nvidia driver, so I don't think I need to install it as some guides have already suggested. It works great, thanks to Hymn and the others :KS 

I sure hope this process isn't that sophisticated. I'm still learning on how to use the Terminal.

---

### Post by TheThinker on 2007-05-15
Okay, so I read up on how to install tarballs and typed ./config for the Beryl-Core package after moving to its directory. I figured that I might be missing a dependant package and thought that it would be easily installed later, but I didn't anticipate this:

[I]checking for LIBBERYLDECORATION... configure: error: Package requirements (xrender >= 0.8.4) were not met:



No package 'xrender' found



Consider adjusting the PKG_CONFIG_PATH environment variable if you

installed software in a non-standard prefix.



Alternatively, you may set the environment variables LIBBERYLDECORATION_CFLAGS

and LIBBERYLDECORATION_LIBS to avoid the need to call pkg-config.

See the pkg-config man page for more details.



megadeuce22@Big-O:~/Desktop/beryl-core-0.2.1$ [/I]


But Synaptic Package manager says that I have the libexrender1 Version: 1:0.9.1-3 already installed. Is this the same xrender the terminal is  talking about? If not, where can I get it? Synaptic Package Manager doesn't list “xrender” itself.

---

### Post by Kobalt on 2007-05-15
I'd suggest you to follow these steps in order to install Beryl easily : [http://ubuntuforums.org/showthread.php?t=357501](http://ubuntuforums.org/showthread.php?t=357501)

---

