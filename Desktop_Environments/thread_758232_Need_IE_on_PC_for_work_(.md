---
title: "Need IE on PC for work :("
date: 2008-04-17
forum: Desktop Environments
---

### Post by metalguy639 on 2008-04-17
I've used the ies4linux package before and it worked just fine, but I'm running into a problem this time. I'm running Hardy 8.04 on the PC and trying to install ies4linux but it keeps on telling me I have the wrong version I need the AMD64 version. So where do I get the AMD64 version? Its not on the typical website so I'm lost as to where to find it.

---

### Post by rainwalker on 2008-04-17
You could try the IEtab extension for Firefox; it will open a page in a tab as if it were being opened with Internet Explorer

---

### Post by warp99 on 2008-04-17
Both supporting packages needed to run ieslinux are available in the universe repository:

[http://packages.ubuntu.com/hardy/wine](http://packages.ubuntu.com/hardy/wine)

[http://packages.ubuntu.com/hardy/cabextract](http://packages.ubuntu.com/hardy/cabextract)

They can be obtained by enabling the universe repository in the Synaptic package manager. After installing the correct packages if ieslinux does not want to install then it's a script error and you need to speak with the developers of ieslinux.

You could also try the Firefox extension User Agent Switcher:

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

This extension will switch the user agent into believing that IE is running instead of Firefox. IE only web is starting to become the exception and not the rule.

---

### Post by metalguy639 on 2008-04-18
> **warp99 said:**
> Both supporting packages needed to run ieslinux are available in the universe repository:

[http://packages.ubuntu.com/hardy/wine](http://packages.ubuntu.com/hardy/wine)

[http://packages.ubuntu.com/hardy/cabextract](http://packages.ubuntu.com/hardy/cabextract)

They can be obtained by enabling the universe repository in the Synaptic package manager. After installing the correct packages if ieslinux does not want to install then it's a script error and you need to speak with the developers of ieslinux.

You could also try the Firefox extension User Agent Switcher:

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

This extension will switch the user agent into believing that IE is running instead of Firefox. IE only web is starting to become the exception and not the rule.

Erm ok I already have wine & cabextract installed I just need the AMD64 package for ies4linux that was the only thing that I could not get to work. I'm a web designer and need to view web pages in IE (which I hate, I think nit should just go away) but I have to make sure pages look right in all browsers. Will this tab thing work for that?

---

### Post by CrazyIndians on 2008-04-19
This one helped a lot. Thanks

---

### Post by warp99 on 2008-04-23
> **metalguy639 said:**
> Erm ok I already have wine & cabextract installed I just need the AMD64 package for ies4linux that was the only thing that I could not get to work. I'm a web designer and need to view web pages in IE (which I hate, I think nit should just go away) but I have to make sure pages look right in all browsers. Will this tab thing work for that?

There is no amd64 package for ies4linux because it's only a script:

> IEs4Linux is the simpler way to have Microsoft Internet Explorer running on Linux (or any OS running Wine).

No clicks needed. No boring setup processes. No Wine complications. **Just one easy script** and you'll get three IE versions to test your Sites. And it's free and open source

[http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

with the option of using pygtk (Gnome) or kommander (KDE) for a GUI install. You can also use the string './ies4linux --no-gui' to install from the command line. Most likely pygtk is giving you problems, so I would install it using the command line arguments.

---

### Post by metalguy639 on 2008-04-23
> **warp99 said:**
> There is no amd64 package for ies4linux because it's only a script:



with the option of using pygtk (Gnome) or kommander (KDE) for a GUI install. You can also use the string './ies4linux --no-gui' to install from the command line. Most likely pygtk is giving you problems, so I would install it using the command line arguments.

That's what I did try from the page that guides you through it in the terminal

---

### Post by danwood76 on 2008-04-23
I dont think IE6 came in 64 bit version, this might be why you cant install it.
You could always run a virtualbox or vmware of xp and check them through that?

---

### Post by metalguy639 on 2008-04-24
> **danwood76 said:**
> I dont think IE6 came in 64 bit version, this might be why you cant install it.
You could always run a virtualbox or vmware of xp and check them through that?

Ok not sure I want to do all that, how do I set that up exactly?

---

### Post by metalguy639 on 2008-04-28
> **danwood76 said:**
> I dont think IE6 came in 64 bit version, this might be why you cant install it.
You could always run a virtualbox or vmware of xp and check them through that?

Actually after I thought about it, it has nothing to do with the AMD setup I have. It worked fine on 7.10 and now it doesn't want to install on 8.04. My sister is running the ie4 linux thing on her PC and she's running a AMD chip & 7.10. Any help would be great on this, thanks

---

### Post by danwood76 on 2008-04-28
Were you running 64 bit ubuntu before ot the 32 bit?
You can un 32 bit OSes on 64 bit hardware.

---

### Post by metalguy639 on 2008-04-28
> **danwood76 said:**
> Were you running 64 bit ubuntu before ot the 32 bit?
You can un 32 bit OSes on 64 bit hardware.

Yeah come to think of it my sister's PC is the 32 bit ubuntu 7.10 and I was running the 32 bit before. :( This really sucks they should have something that will work in the 64 bit one :(

---

### Post by danwood76 on 2008-04-28
You could run windows under VMware Server or Virtual Box to test out your web pages.
You can then try them out in the latest version of IE also.

---

### Post by metalguy639 on 2008-04-28
> **danwood76 said:**
> You could run windows under VMware Server or Virtual Box to test out your web pages.
You can then try them out in the latest version of IE also.

How do I do that?

---

### Post by zammit on 2008-05-01
I'm running Ubuntu 8.04 amd64 and successfully installed IE6 IE5.5 and IE5 using ies4linux. Download the ies4linux-latest.tar.gz, extract then run the following command:
```

./ies4linux --no-gui --install-ie55 --install-ie5

```
I could not get any other versions (7, 1, 1.5 & 2) nor the corefonts (but if you have the mscorefonts package installed you don't need that).

Now getting them to work as smoothly as I'd like is another story. I can open the browsers and it will successfully build the home page but I cannot get it do anything else =S it seems like it locks up.

**Update:**
Everything is working just fine now... I did a "reinstall" on top of the existing one. Then ran *ie6* from the terminal.

Did summore digging and I've got multiple IEXPLORER.EXE processes running. Also when running from terminal and then closing the browser, the terminal hangs.

---

### Post by metalguy639 on 2008-05-02
I'll give that a try and see how it works for me.

---

### Post by kforum on 2008-05-08
i got everything installed in 8.04 all i did was --no-gui --beta-install-ie7.
or the likes ;)

---

