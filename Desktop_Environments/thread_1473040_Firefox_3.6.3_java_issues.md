---
title: "Firefox 3.6.3 java issues"
date: 2010-05-04
forum: Desktop Environments
---

### Post by bgvianyc on 2010-05-04
I recently upgraded to 10.04 from karamic, and now I can not run java applets in firefox 3.6.3 which is part of the OS, although they run in the chrome browser. Any ideas why firefox is not running the java applets?

---

### Post by moongia on 2010-05-04
> **bgvianyc said:**
> I recently upgraded to 10.04 from karamic, and now I can not run java applets in firefox 3.6.3 which is part of the OS, although they run in the chrome browser. Any ideas why firefox is not running the java applets?

i had to add the sun-Java6 Plug-in in the synaptic and remove all the openJDK stuff for my java to work..

---

### Post by infamous-online on 2010-05-04
> **moongia said:**
> i had to add the sun-Java6 Plug-in in the synaptic and remove all the openJDK stuff for my java to work..

Where is the sun plugin at I haven't seen it yet?

---

### Post by AbangBoltok on 2010-05-04
hmm...

i still got mine working after upgrading from karmic koala.

as i remember i used this sudo command:

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

enter password, if there is an agreement, just select yes.
and after that there will be something like EULA or sth that u dont need to worry about, and then select ok.

u know what to do...

just enter that sudo command. 

and after doing that, go to your Firefox and type "about:plugins" in URL bar.
i'm not sure on chrome. but probably "chrome:plugins". (i'm not on my computer right now so i'm not really sure) :D
if you can see  a list of multiple java....***** then you can try to use the applet on your browser.

or maybe you can try this:
[http://ubuntuforums.org/showthread.php?t=1113039](http://ubuntuforums.org/showthread.php?t=1113039)

---

### Post by moongia on 2010-05-04
> **infamous-online said:**
> Where is the sun plugin at I haven't seen it yet?

you may need to add the ''lucid partner'' in your software sources and then reload your synaptic..i do remember having to remove the openJDK to get limewire to work as well.

---

### Post by lovinglinux on 2010-05-05
[http://sites.google.com/site/easylinuxtipsproject/java]("http://sites.google.com/site/easylinuxtipsproject/java")

---

### Post by infamous-online on 2010-05-05
> **moongia said:**
> you may need to add the ''lucid partner'' in your software sources and then reload your synaptic..i do remember having to remove the openJDK to get limewire to work as well.

Wow, I've been doing it the hard way when I could have done this instead. Thanks for the help!Also I notice your windows are transparent, what skin is that?

---

### Post by moongia on 2010-05-05
> **infamous-online said:**
> Wow, I've been doing it the hard way when I could have done this instead. Thanks for the help!Also I notice your windows are transparent, what skin is that?

You got it going kool,,,ok the theme im using is called "airlines"i got it with "ubuntu tweak"its apart of bisigi theme project.as for the glass window border,I use "emerald",its a window theme manager.to install it i would just go in to the synaptic and type "compiz" and look for "emerald" and "fusion-icon" install the two,and use the fusion-icon to turn on emerald.From there go online to gnome look and find some themes for emerald.the one you see is called "Tinted Glass v.0.3".but sometimes with emerald when you login to your desktop,you will be missing your window borders,buttons and all.what works for me is to type "compiz" in the Terminal to get it back..hope this helps...

---

