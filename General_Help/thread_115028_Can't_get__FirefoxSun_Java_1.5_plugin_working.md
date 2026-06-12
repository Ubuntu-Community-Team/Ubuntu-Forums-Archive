---
title: "Can't get  Firefox/Sun Java 1.5 plugin working"
date: 2006-01-09
forum: General Help
---

### Post by rick333 on 2006-01-09
I've tried both recommended methods of getting Sun JDK 1.5 installed and I'm having problems with both. I'm running breezy 5.10 with Firefox 1.0.7 with the k7-smp linux kernel.

First, I tried the following:

  1. Installed java-package using Synaptic
  2. Downloaded Sun JDK 1.5 rpm package - jdk-1_5_0_06-linux-i586-rpm.bin
  3. fakeroot make-jpkg  jdk-1_5_0_06-linux-i586-rpm.bin

This failed with the following output:

```

rick@thinkmate:~/install.dsk/jdk$ fakeroot make-jpkg jdk-1_5_0_06-linux-i586 -rpm.bin
Creating temporary directory: /tmp/make-jpkg.XXXXaNAWKB
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm- j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun- j2sdk.sh
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)

No matching plugin was found.
Removing temporary directory: done

```

I couldn't figure out what the problem is with this -- anyone know? so I tried the other alternative:

  1. Installed alien package using Synaptic
  2. chmod +x jdk-1_5_0_06-linux-i586-rpm.bin
  3. ./jdk-1_5_0_06-linux-i586-rpm.bin
  4. alien jdk-1_5_0_06-linux-i586-rpm
  5. sudo dpkg -i jdk_1.5.0_06-1_i386.deb

Everything looks ok at this point, so I set up the Firefox plugin link from

  cd /usr/lib/mozilla-firefox/plugins/
  sudo ln -s /usr/java/jdk1.5.0_06/jre/plugin/i386/ns7/libjavaplugin_oji.so

This setup the link to the plugin, but the plugin doesn't work. I went to this Java Tutorial page to check it out:
[http://java.sun.com/docs/books/tutorialJWS/uiswing/components/example-1dot4/ScrollDemo.jnlp](http://java.sun.com/docs/books/tutorialJWS/uiswing/components/example-1dot4/ScrollDemo.jnlp)

Firefox pops up a dialog box that asks me to choose an application to open. It recognizes the .jnlp type as a "Java Network Launched Application", but doesn't find the plugin. 

I restarted Firefox...I even rebooted and got the same result. The Firefox plugins dialog shows no .jnlp file type.

Also, I discovered the /etc/alternatives directory. Not sure whether I should pay any attention to this, and if so, what is the recommended approach to change the alternatives settings to reflect my preferred Java system?

Preferably, I would like to setup the Sun 1.5 JDK as my default Java system for running, compiling, etc. I don't see any need for the GNU Java implementation at the moment. Should/can I just uninstall these GNU Java packages or will that break something else?

Thanks very much for help... Rick

---

### Post by dcstar on 2006-01-09
[QUOTE=rick333]I've tried both recommended methods of getting Sun JDK 1.5 installed and I'm having problems with both. I'm running breezy 5.10 with Firefox 1.0.7 with the k7-smp linux kernel.
......
Preferably, I would like to setup the Sun 1.5 JDK as my default Java system for running, compiling, etc. I don't see any need for the GNU Java implementation at the moment. Should/can I just uninstall these GNU Java packages or will that break something else?

Thanks very much for help... Rick[/QUOTE]
If you can live with the previous 05 update SDK, add this line to you sources.list and install via Synaptic:

deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free

---

### Post by rick333 on 2006-01-10
I installed the JDK from: 

deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free

The SDK installed into /usr/lib, but still no plugin support for Firefox and I still get gij (GNU libgcj Java) as my default in /usr/bin/java. I added a symbolic link to libjavaplugin_oji.so from /usr/lib/mozilla-firefox directory and removed the link I had there before for the Java plugin. Still no response when I click on a .jnlp file in a web page. Yes, I did restart Firefox.

I'm stumped. I've done this before with other Linux distributions and the Java plugin just worked. 

Unless someone out there can offer a better suggestion, I plan to add /usr/lib/j2sdk1.5-sun to the beginning of my PATH in .bashrc in my home directory to make the Sun 1.5 JDK my default. Any other (better) recommendations?

Of course, I still need to solve this Firefox Java plugin problem. Any ideas?

Thanks... Rick

---

### Post by neels on 2006-01-11
try this one: [http://www.ubuntuforums.org/showthread.php?t=76754](http://www.ubuntuforums.org/showthread.php?t=76754)

---

### Post by rick333 on 2006-01-12
[QUOTE=neels]try this one: [http://www.ubuntuforums.org/showthread.php?t=76754](http://www.ubuntuforums.org/showthread.php?t=76754)[/QUOTE]

Well, after following these instructions and some additional piddling around, my Java plugin works! Thanks. Actually, I had been aware of that alternative and had been trying not to employ it because I wanted to use only .deb packages. 

I'm still not off this topic though, because I'm still seeing the following behavior that puzzles me:

1. Before I ran the JDK 1.5 .bin installer, I tried various combinations of linking the Java plugin to Firefox. I tried (I think) all combinations of direct linking to the Java plugin .so and indirectly linking through the /etc/alternatives from both the /usr/lib/mozilla and /usr/lib/mozilla-firefox plugin directories. These links were all directed to the Java .so plugin file in the n7 plugins directory under /usr/lib/j2sdk1.5-sun. None of these alternatives worked.

2. I then deleted all the Java plugin links in both the mozilla and mozilla-firefox plugin directories, and ran the JDK 1.5 .bin installer (I installed into /usr/local/lib). I restarted Firefox and it loaded the Java plugin when I clicked on a .jnlp link in one of the Java Tutorial pages....as expected!

3. I then tried to access my brokerage account which has a real-time ticker Java applet. However, when I clicked on the link to launch this applet (which does not use a .jnlp file...it uses a link that ends in "default.aspx#") When I clicked on this link, I was prompted to install the Java plugin...hmmm. The strange thing is that when I couldn't get Firefox to launch the Java plugin from a .jnlp link, this ticker applet had been working. 

4. I then figured I'd the links to my other Sun JDK installation via /etc/alternatives, which I did from both mozilla and mozilla-firefox plugin directories. My ticker applet again started to work. Strange and I don't understand why. Anyone?

5. Finally, I still haven't figured out the make-jpkg problems described earlier in this thread. I'd really prefer to install the Java plugin that way -- so I can manage it, upgrade, etc. more effectively.

All said, however, the Sun JDK 1.5 is now operational, so I will get back to more important things. But if anyone has anything to add to my little mystery here, I am still very much interested to hear more ideas.

Thanks.... Rick

---

