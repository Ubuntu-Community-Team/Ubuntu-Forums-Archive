---
title: "Webex does not work"
date: 2009-01-06
forum: General Help
---

### Post by sergm on 2009-01-06
Webex does not work in FF in Ubuntu 8.10.

I got this:

Java Not Enabled

Meeting Center cannot be installed because Java is disabled in your Web browser. Please enable Java in your browser, and then click Set Up again. For instructions on enabling Java, refer to your browser's online help.

If Java cannot be enabled for any reason, you can download the manual installer and install it from your desktop by double-clicking the installer icon.

I have verified that the checkbox in preferences for Java is enabled.

Any ideas?

Thanks,
Sergei

---

### Post by nikgare on 2009-01-06
Java is not the same as Javascript!

For Java you need to install the java plugin:

sudo aptitude install sun-java6-plugin

Restart firefox and type **about:config** in the url bar to check if it's been installed correctly

---

### Post by sergm on 2009-01-06
yeah. I'm aware that Java is not Javascript :)

if you check Edit -> Preferences in FF then you'll see a checkbox for both Javascript and Java.

Anyways, thanks for the tip, I've installed plugin and now it's hanging on 52% and doint nothing.

Webex told me that they don't support Ubuntu 8.10 / FF 3 :(

thanks

---

### Post by timcredible on 2009-01-06
i just tried their demo, works fine, i'm using 8.10 with ubuntu-restricted-extras installed for java

---

### Post by sergm on 2009-01-06
> **timcredible said:**
> i just tried their demo, works fine, i'm using 8.10 with ubuntu-restricted-extras installed for java

thanks for this!
could you please let me know how to install those restricted extras for java?

I've tried to search for "ubuntu-restricted-extras java" in synaptic but that doesn't show up anything obvious...

I have sun-java6-jre and jdk installed...

Thanks for you help!

---

### Post by sergm on 2009-01-06
I can see a package called: ubuntu-restricted-extras

but there is nothing specifically about java in this package...

---

### Post by dave100 on 2009-03-04
> **timcredible said:**
> i just tried their demo, works fine, i'm using 8.10 with ubuntu-restricted-extras installed for java

Doubt it. How far did you go with your test?
I can join a meeting (ubuntu-restricted-extras helped with that). Everything looks ok but I can not see any shared applications, only shared documents. When presenter shares an application, it opens just a black window for me. And I think that is a major problem with this kind of service.

Has anyone got viewing of shared application working with any version of Ubuntu?

---

### Post by sergm on 2009-03-04
I have the same issue and moreover, I can't start my own meeting as well.

It just hangs at 100% in FF and that's it.

I've opened a ticket with Webex and all they told me was:

Ubuntu 8.10 is currently not in the list of supported platforms :(

Sheesh...

p.s. What I do for the work-around is: login remotely to Win XP box and start webex from there.

that's bad...that's really frustrating...

---

### Post by Rebootkid on 2009-03-16
I eventually got it working.
ubuntu-restricted-extras
sun-java6-plugin
libstdc++5

I had to install all of those, restart firefox, and I was good to go.
Someone talked about exporting the java path and java home, but that didn't work for me.

---

### Post by sergm on 2009-03-17
> **Rebootkid said:**
> I eventually got it working.
ubuntu-restricted-extras
sun-java6-plugin
libstdc++5

I had to install all of those, restart firefox, and I was good to go.
Someone talked about exporting the java path and java home, but that didn't work for me.

interesting. are you on ubuntu 8.10?
I still can't get it to work.

I have all the same packages already installed and when I click to start a meeting it goes to 100% and then just hangs and nothing happens. :(

---

### Post by alex.burlacu on 2009-04-06
Hi,
I've just made it working on my intrepid:

Here are the steps i have done

1. sudo apt-get install libstdc++5 sun-java6-plugin
2. Edit your ~/.profile and add these two lines:
export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.66
export PATH=$JAVA_HOME/bin:$PATH
3. Restart X by logging off/on

Good Luck
Alex

__________
You can be anything you want to be
Just turn yourself into anything you think that you could ever be
Be free with your tempo, be free be free
Surrender your ego - be free, be free to yourself 
[http://alex.burlacu.blogsite.org/blog]("http://alex.burlacu.blogsite.org/blog")

---

### Post by sergm on 2009-04-10
Thanks but still does not work for me on Ubuntu 8.10

I have exactly the same packages installed already.

When I login to webex and click on one-click meeting it starts an applet! and it goes to 100% and then just hangs and nothing happens:(

sigh

---

### Post by rkrishnam_can01 on 2009-05-14
In my case I got a message 'applet loading' and went upto 65% and got stuck.

---

### Post by sh2d35 on 2009-05-25
> **Rebootkid said:**
> I eventually got it working.
ubuntu-restricted-extras
sun-java6-plugin
libstdc++5

I had to install all of those, restart firefox, and I was good to go.
Someone talked about exporting the java path and java home, but that didn't work for me.

This seems to work for me too although I thought libstdc++6 was enough but it looks like libstdc++5 is needed as well!

Video is still not working though! any idea on how to fix that?

---

