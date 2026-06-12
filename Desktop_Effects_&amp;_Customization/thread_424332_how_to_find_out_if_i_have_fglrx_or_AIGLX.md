---
title: "how to find out if i have fglrx or AIGLX"
date: 2007-04-26
forum: Desktop Effects &amp; Customization
---

### Post by kystorms on 2007-04-26
I have the ATI 7000 ve , and I would like to try my hand now that i am a bit more comfortable with Dapper AT getting Beryl on my PC. I have read so many different how tos, here are my questions:
1. how do i find out if i have fglrx or AIGLX on here?

2. What do I do to get beryl, after I find out which of the above I have, can someone please point me to a how to on how to get Beryl?

thanks
:confused:

---

### Post by regal_dunce on 2007-04-27
> **kystorms said:**
> I have the ATI 7000 ve , and I would like to try my hand now that i am a bit more comfortable with Dapper AT getting Beryl on my PC. I have read so many different how tos, here are my questions:
1. how do i find out if i have fglrx or AIGLX on here?

I'm pretty sure than AIGLX is not enabled by default in dapper.  If you upgrade to edgy or feisty then it is.  If you want to find out if you have flgrx installed, simply type "fglrxinfo" (without quotes) into the terminal.  If it's a recognized command, you have fglrx.  If not, you need to install it.  

> 
2. What do I do to get beryl, after I find out which of the above I have, can someone please point me to a how to on how to get Beryl?

In terms of getting beryl, your first step should be to enable 3D acceleration from your video card.  See ATI's website for how to do this:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")

After that's done, there are some very excellent, comprehensive howto's on how to install beryl on these forums. If you're looking for a different one, you can go to the beryl project's website, where there's a dapper howto:

[http:///wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Dapper_with_XGL]("http:///wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Dapper_with_XGL")

Good luck!

---

### Post by Styx on 2007-04-27
I think that the AIGLX is not supported by the ATI driver. How ever XGL schould work. 
You have to download the ATI driver from the home page to do so you can follow this link. 

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

try to use the manual way there it is more sure that it will worke. Dit for me.
Then you can use the following link to install your beryl.

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL)

---

