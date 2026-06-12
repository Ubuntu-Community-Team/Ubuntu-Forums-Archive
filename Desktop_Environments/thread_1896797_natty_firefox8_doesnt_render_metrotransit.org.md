---
title: "natty firefox8 doesnt render metrotransit.org"
date: 2011-12-17
forum: Desktop Environments
---

### Post by gregwm on 2011-12-17
natty firefox 8.0+build1-0ubuntu0.11.04.3 doesn't render [metrotransit.org]("http://metrotransit.org/"), it offers to download an .aspx file instead, my best guess is the [metrotransit.org]("http://metrotransit.org/")  main page is lacking metadata describing how to properly render it, but  still, every other browser, and even  firefox8 on other platforms, all render [metrotransit.org]("http://metrotransit.org/") just fine.

i tried "help->report a problem", it gobbled a whopping 2g of  memory, then complained it couldn't reach the online crash database,  offhand i'd guess that was due to significant lag due to thrashing, i've  "only" got 1g ram.


then i tried "submit feedback", it complained "Ensure this value has at most 140 characters (it has 509)."


then, in the firefox support forum.  on page: [http://support.mozilla.com/en-US/questions/new?category=d1&product=desktop](http://support.mozilla.com/en-US/questions/new?category=d1&product=desktop) clicking the link: "Firefox cannot load websites but other programs can" gets "Page Not Found"

reminds me of fukushima.  when things are fine, they're fine.    when things start to go awry, well, stand back!


 i did submit this in the firefox help forum, and the answer i got was "if you use an Ubuntu branded Firefox build then you need to ask advice on the Ubuntu forum."

---

### Post by lovinglinux on 2011-12-18
The site is not recognizing Firefox 8,9 or 10 on Linux.

It works with Firefox 6 and 7.

I tried to change the user agent with [User Agent Switcher](https://addons.mozilla.org/en-US/firefox/addon/59/) and it works, but the site redirects to the mobile version.

---

### Post by gregwm on 2011-12-18
> **lovinglinux said:**
> The site is not recognizing Firefox 8,9 or 10 on Linux.

reports are ff8:metrotransit.org fails on natty, mint, Bodhi, but works on fedora 16, PlaxOS, openSUSE 11.4.

perhaps due to useragent settings?

---

### Post by lovinglinux on 2011-12-18
> **gregwm said:**
> reports are ff8:metrotransit.org fails on natty, mint, Bodhi, but works on fedora 16, PlaxOS, openSUSE 11.4.

perhaps due to useragent settings?

Is the web site fault. It doesn't recognize the user agent string properly.

Perhaps you could change the user agent string to openSUSE 11.4 and test it.

---

### Post by jockyburns on 2011-12-18
Loads just fine on Google Chrome and Natty 11.04

---

### Post by lovinglinux on 2011-12-24
Tested [User Agent RG](https://addons.mozilla.org/en-US/firefox/addon/user-agent-rg/), selected Chrome 11 agent and it worked.

---

### Post by Frogs Hair on 2011-12-24
The site opens in Opera and is offered as a document download in Nightly .

---

### Post by Karlchen on 2011-12-24
Looks as if the source of trouble has been fixed. Have just opened [http://metrotransit.org/](http://metrotransit.org/) without experiencing any problem.

Ubuntu Desktop 10.04.3 32-bit
Firefox 9.0.1

Will try the same using Firefox 9.0.1 on Mint 12, 32-bit (definitely based on Oneiric Ocelot, i.e. Ubuntu 11.10) and report back in case it should _not_ work.
 
Karl

---

### Post by lisati on 2011-12-24
Interesting: I checked the website with ff8, and was asked to download an XML file.

---

### Post by sammiev on 2011-12-24
> **lisati said:**
> Interesting: I checked the website with ff8, and was asked to download an XML file.

Just checked it out with FF10 and was asked to download an XML file.

---

### Post by lovinglinux on 2011-12-24
It is working for me know with FF 9, 10, 11 and 12.

---

### Post by Karlchen on 2011-12-24
Hi, folks.

Have just tried it using Firefox 9.0.1 on Mint 12 (Ubuntu 11.10). And guess what? It does not work. Firefox asks me to download a default.aspx file instead of displaying the webpage.

The download box identifies an object classified as "application/vnd.wap.xhtml+xml". WAP? Hm ...
The user-agent string does not mention any tablet device or OS: "User-Agent: Mozilla/5.0 (Ubuntu; X11; Linux i686; rv:9.0.1) Gecko/20100101 Firefox/9.0.1". Looks all right to me.

So what might be the reason? What is the difference between my
+ Firefox 9.0.1 on Lucid Lynx and
+ Firefox 9.0.1 on Mint 12 "Lisa"?

Firefox 9.0.1 on Lucid Lynx originally was Firefox 8.0.1 which I had downloaded and installed by using the [Ubuntuzilla repositories]("http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation"). (sources.list entry: deb [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main) Yesterday, this Firefox 8.0.1 was updated to Firefox 9.0.1 by using the automatic update function built-in to Firefox. Anyway, this Firefox 9.0.1 is the unmodified Firefox provided by Mozilla. It displays the webpage just fine.

Firefox 9.0.1 on Mint 12 "Lisa" originally was Firefox 8.0 as delivered by the original Mint 12 installation ISO file. It has been updated to Firefox 9.0.1 only today by using the [Ubuntu PPA repository]("http://www.noobslab.com/2011/12/install-firefox-9-on-ubuntu.html"). (sources.list entry: deb [http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu) oneiric main) This Firefox 9.0.1 refuses to display the webpage and instead offers to download some file.

This suggests that there must be something wrong with the Firefox provided by the Ubuntu Mozilla Security PPA. This may just be an incorrect configuration setting. This may be some more severe flaw. I do not know yet.

Kind regards,
Karl

---

### Post by lovinglinux on 2011-12-24
> **Karlchen said:**
> 
This suggests that there must be something wrong with the Firefox provided by the Ubuntu Mozilla Security PPA. This may just be an incorrect configuration setting. This may be some more severe flaw. I do not know yet.

Try to disable Ubuntu Firefox Modifications extension.

---

### Post by Karlchen on 2011-12-24
Hello, lovinglinux.

My user-agent string is "User-Agent: Mozilla/5.0 (Ubuntu; X11; Linux i686; rv:9.0.1) Gecko/20100101 Firefox/9.0.1". This is what webpages will be told. And it seems to be correct as far as I can tell.

And as I am on a slightly modified Oneiric Ocelot, which is named Mint 12 Lisa, there is no Ubuntu Firefox Modifications extension.

Instead there is:
+ Global Menu Bar Integration 2.0.2 (for Unity integration) ... activated
+ Mint Search Enhancer 1.0 (for enhanced Google results) ... activated
+ Stylish 1.0.7 ... DE-ACTIVATED because incompatible with Firefox 9.0.1

Kind regards,
Karl
--
_ P.S.1:_
Switched the first two extensions off as well and restarted Firefox. Not quite sure what I have lost now, if anything at all ...
--
_P.S. 2:_
May have lost nothing. But have not gained anything, either. Same behaviour as before.
I still have got the vague feeling it might be the user-agent string "User-Agent: Mozilla/5.0 (Ubuntu; X11; Linux i686; rv:9.0.1) Gecko/20100101 Firefox/9.0.1" which the webpage [http://metrotransit.org/](http://metrotransit.org/) mis-interprets, though it seems to conform to the rules. Whereas the Opera user-agent string, "User-Agent: Opera/9.80 (X11; Linux i686; U; Edition Linux Mint; de) Presto/2.10.229 Version/11.60", does not, but does the trick and Opera gets serviced properly.
--
_P.S. 3:_
Back on Lucid Lynx and using Mozilla Firefox 9.0.1, the webpage [http://metrotransit.org/](http://metrotransit.org/) is displayed fine. The genuine Mozilla Firefox 9.0.1 uses the user-agent string "Mozilla/5.0 (X11; Linux i686; rv:9.0.1) Gecko/20100101 Firefox/9.0.1". 
In case the user-agent string makes the difference, then dropping the "Ubuntu" part on the Mint 12 machine should do the trick.
How do I persuade Firefox to do so? ... Oh, I see, [User Agent RG]("https://addons.mozilla.org/en-US/firefox/addon/user-agent-rg/") might help.

---

### Post by Karlchen on 2011-12-25
Hello, gregwm.

I assume _**the source of trouble**_ has been positively identified:
As has been explained in this thread before, the affected **webpage [http://metrotransit.org/](http://metrotransit.org/) incorrectly parses the [B]user-agent **string[/B] which Firefox passes to them.
As has been explained, too, this does not happen e.g. when you use the original Firefox 9.0.1 provided on the Mozilla download pages or the one provided by Ubuntuzilla.
The original Mozilla Firefox 9.0.1 uses this user-agent string: **Mozilla/5.0 (X11; Linux i686; rv:9.0.1) Gecko/20100101 Firefox/9.0.1**
The Ubuntu Firefox 9.0.1, however, uses this user-agent string: **Mozilla/5.0 (Ubuntu; X11; Linux i686; rv:9.0.1) Gecko/20100101 Firefox/9.0.1**

As can be seen the difference is just the string "Ubuntu" which is absent from the Mozilla user-agent string.

_**Workaround:**_

So the workaround is pretty simple: Make the Ubuntu Firefox 9.0.1 use the same user-agent string as the original Mozilla Firefox:
[LIST]
[*]Inside Firefox go to **about:config**.
[*]Confirm that you will be careful.
[*]In the **Filter** edit field enter: **general.useragent**. This will make **about:config** limit its display to parameters starting with **general.useragent**.
[*]In case the parameter **general.useragent.override** exists double-click on it to modify it. In the edit box enter the following user-agent string: **Mozilla/5.0 (X11; Linux i686; rv:9.0.1) Gecko/20100101 Firefox/9.0.1** and confirm.
[*]In case the parameter **general.useragent.override** does not exist right click any of the other paramters and select **New** => **String**.
In the first edit field enter the parameter name **general.useragent.override** and confirm.
In the second edit field enter the following user-agent string: **Mozilla/5.0 (X11; Linux i686; rv:9.0.1) Gecko/20100101 Firefox/9.0.1** and confirm.
[*]Close **about:config**.
[*]_Note:_
For users of Firefox 8.0.1 the user-agent string will read **Mozilla/5.0 (X11; Linux i686; rv:8.0.1) Gecko/20100101 Firefox/8.0.1**
[*]In order to verify that Firefox uses the added/modified user-agent string visit e.g. [http://whatsmyuseragent.com/](http://whatsmyuseragent.com/)
[*]In order to verify that the modified user-agent string has solved the initial problem visit [http://metrotransit.org/](http://metrotransit.org/). It should be displayed without any problems now.
[/LIST]
 
[U]Downside of the workaround:
[/U]
Next time you update to a newer Firefox version you will have to change the parameter **general.useragent.override** yourself manually to reflect the update, or your Firefox will go on identifying itself as the older version.

HTH, Merry XMas and kind regards,
Karl

---

### Post by gregwm on 2011-12-25
danke schön karl.  excellently written.  workaround verified.  Fröhliche Weihnachten.

---

### Post by Karlchen on 2011-12-25
Hi, gregwm.

You're welcome. :) Glad to learn the problem has been worked around successfully. 

Karl

---

### Post by ryanm406638 on 2012-01-25
That did it for me too.  My problem was loading pnfp.com.  My bank's website.  That solved the problem.

---

