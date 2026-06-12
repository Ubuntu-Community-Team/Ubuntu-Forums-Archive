---
title: "Firestarter Firewall"
date: 2009-03-29
forum: General Help
---

### Post by accooper on 2009-03-29
How do I get Firestarter Firewall To start up when ubuntu starts up?

BTW All Of You Have been very helpful and I thank you all.

:guitar:

Andrew

---

### Post by lovinglinux on 2009-03-29
I guess there are a few different ways. When I used Firestater, I added it to the session. Anyways, [http://www.google.com/search?q=Firestarter+root+gui+security+site%3Aubuntuforums.org&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=Firestarter+root+gui+security+site%3Aubuntuforums.org&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

Several people will post here that you shouldn't use Firestarter, for security reasons. So let me start :) The recommended firewall manager now is ufw (gufw for GUI).

---

### Post by HermanAB on 2009-03-30
Also note that Firestarter and UFW don't really do anything useful.  You only need to run them once to configure the firewall.  You don't need to run them again.  The firewall is a set of Linux kernel modules known as Netfilter and once configured it it always runs.

---

### Post by lovinglinux on 2009-03-30
> **HermanAB said:**
> Also note that Firestarter and UFW don't really do anything useful.  You only need to run them once to configure the firewall.  You don't need to run them again.  The firewall is a set of Linux kernel modules known as Netfilter and once configured it it always runs.

And running it all the time is a security risk, due to root privilege requirement to run it.

---

### Post by accooper on 2009-03-30
Thanks for the info!

:guitar:

Andrew

---

### Post by hyper_ch on 2009-03-30
are you sure you need to mess with iptables? In most cases there's no need for it.

---

### Post by eddski on 2009-04-06
So if I'm understanding you right, you really don't need firestarter or ufw since they are just front ends for iptables?

---

### Post by mb_webguy on 2009-04-06
Firestarter and ufw are front-ends for iptables, yes.  I'm not sure that means that you don't need them.  iptables itself is pretty spartan, so *iF* you're going to be manipulating iptables, a front-end can be nice.  However, this *does* mean that you don't have to run Firestarter constantly for you to be protected by iptables.

On the other hand, most people don't really *need* to mess around with iptables.  If you don't have any servers running, then all of your ports are closed.  And if you *do* have some kind of server running, you generally don't want a firewall blocking the ports it uses.  All ports on a default installation of Ubuntu are closed, and there's no functional difference between a closed port and a port stealthed by a firewall -- no one is getting into your system either way.

Anyone thinking of changing the firewall settings on Ubuntu should probably read the link in my signature about security on Ubuntu (or [Bodhi's more comprehensive thread]("http://ubuntuforums.org/showthread.php?t=510812") on the subject) first.

---

### Post by Daremo_06 on 2009-04-06
> **lovinglinux said:**
> And running it all the time is a security risk, due to root privilege requirement to run it.

Doesn't that defeat the entire purpose of having a firewall?  Its suppose to isolate one network or computer system from others from unauthorized access either inadvertent or intentional (read malicious) by controlling who has access to various ports.  Or at least thats what I thought... :)

Currently I am chasing down a problem with Firefox crashing on my x64 Intrepid system that I just setup via fresh install middle of last week.  One of the potential hints I have to this is some errors in the log for Firefox that some of my research has indicated might be incorrect security settings on a firewall.  I am running a router, so normally I don't enable a desktop's because I use the one on the router.  If I didn't specifically download Firestarter or any other firewall program, then there is none in a normal x64 8.10 correct?

Thanks

---

### Post by hyper_ch on 2009-04-06
firestarter is no firewall.

---

### Post by madman100 on 2009-04-06
hi accooper here a working  guide that i use 

Step 1
In terminal type:
export EDITOR=gedit && sudo visudo
That will open /etc/sudoers

Step 2
In /etc/sudoers replace the line "defaults" from:
Defaults !lecture,tty_tickets,!fqdn
to
Defaults !lecture,tty_tickets,!fqdn,env_keep+="DISPLAY HOME"

Step 3
add this line at the *very end* of the /etc/sudoers :
username ALL= NOPASSWD: /usr/sbin/firestarter
make sure to replace username with your username!
Then save and exit Gedit.

Step 4
Navigate to:
System > Preferences > Sessions >new startup program
Give it a name like "Firewall" or "Firestarter"
then use this command:
sudo /usr/sbin/firestarter --start-hidden

---

### Post by hyper_ch on 2009-04-06
madman100:

that's really bad advice.

---

### Post by phantom3113 on 2009-04-06
> **hyper_ch said:**
> madman100:

that's really bad advice.

Seconded. O_o

---

### Post by Daremo_06 on 2009-04-06
> **hyper_ch said:**
> firestarter is no firewall.

Uhh ok.. then could you explain what it is?  Because it certainly is described as one in the following links.

From the documentation page:

[https://help.ubuntu.com/8.10/keeping-safe/C/firewall.html](https://help.ubuntu.com/8.10/keeping-safe/C/firewall.html)

and then from google:

[http://searchenterpriselinux.techtarget.com/sDefinition/0,,sid39_gci1129486,00.html](http://searchenterpriselinux.techtarget.com/sDefinition/0,,sid39_gci1129486,00.html)
[http://linux.about.com/cs/linux101/g/firestarter.htm](http://linux.about.com/cs/linux101/g/firestarter.htm)

---

### Post by hyper_ch on 2009-04-06
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by Daremo_06 on 2009-04-06
Ah thank you!  I see where you draw the distinction in this paragraph taken from that guide.

"A source of confusion sometimes occurs when users feel the need to be running firestarter/Guarddog for their firewall to be active. This is untrue ! Keep in mind that these applications are not firewalls, but rather configuration tools for ip tables. These applications should be run only to configure your firewall. Once configured, IP tables (the actual firewall) is active (at boot) without having to run firestarter/guarddog. firestarter will monitor traffic, but it runs as root and there are better monitoring programs, so configure you firewall, shut down firestarter/grauddog, and let IP tables do the rest"

So that brings me back to my original question...

Could my new installation need to have one of those applications run to ensure my configuration is correct and not causing Firefox to have an issue with certain websites running flash/java (haven't ironed it down yet which, but I think its flash)?

---

### Post by hyper_ch on 2009-04-06
how do you connect to the internet?
What dangers are you afraid of that you think you need to modify the default rules in iptabels?

---

### Post by Daremo_06 on 2009-04-06
> **hyper_ch said:**
> how do you connect to the internet?
What dangers are you afraid of that you think you need to modify the default rules in iptabels?

Through a router and then onto local cable internet.

I am not afraid of a particular danger, instead I am trying to resolve an issue between firefox and flash/javascripts which causes firefox to crash as if I killed it.  It usually happens on sites like facebook or often times in various forums that have additional flash/javascript ads ect ect on them.  I found a post last night referring to a possible issue with a port or ports not being configured to allow firefox to work properly.  It results in an error in the log and the browser up and vanishing.  So that's what I am doing.

---

### Post by lovinglinux on 2009-04-06
> **Daremo_06 said:**
> Through a router and then onto local cable internet.

I am not afraid of a particular danger, instead I am trying to resolve an issue between firefox and flash/javascripts which causes firefox to crash as if I killed it.  It usually happens on sites like facebook or often times in various forums that have additional flash/javascript ads ect ect on them.  I found a post last night referring to a possible issue with a port or ports not being configured to allow firefox to work properly.  It results in an error in the log and the browser up and vanishing.  So that's what I am doing.

That problem with flash has nothing to do with ports. If a port is closed, the worst that can happen is the content not being displayed.  I doubt is the case, otherwise you wouldn't be able to browse any site, because most browser traffic will go through ports 80 and 443, independently of content type. Additionally, the default Ubuntu installation allow all traffic, so installing Firestarter and messing with the iptables wouldn't solve any flash/java issues, even if that assessment is correct.

Anyway, could you please provide the link to that post. I wanna take a look, because this sounds really weird. I never heard anything like that.

---

### Post by Daremo_06 on 2009-04-06
Okay here is the link I had found last night.  

[http://support.mozilla.com/tiki-view_forum_thread.php?locale=tr&forumId=1&comments_threshold=0&comments_parentId=212585&comments_offset=0&comments_per_page=20&thread_style=commentStyle_plain](http://support.mozilla.com/tiki-view_forum_thread.php?locale=tr&forumId=1&comments_threshold=0&comments_parentId=212585&comments_offset=0&comments_per_page=20&thread_style=commentStyle_plain)

It doesnt specifically address linux builds, but I am not sure that the problem I have is actually linux in nature...

Here is an example of the warnings I am seeing in the Firefox Error console.

Warning: Expected declaration but found '*'.  Skipped to next declaration.
Source File: [http://support.mozilla.com/minify.php/css_styles_mozcommon;css_styles_mozfr](http://support.mozilla.com/minify.php/css_styles_mozcommon;css_styles_mozfr)
Line: 1

---

### Post by wrose51106 on 2009-04-06
To break it down so I understand and everyone else.

During boot, IPTABLES auto loads already, IPTABLES is your firewall. You are good to go.

You can install firestarter, which is a gui to help you modify IPTABLES, which most people do not need to even mess with. There is no point to even install firestarter for most people. 

-Bill

---

### Post by lovinglinux on 2009-04-06
> **Daremo_06 said:**
> Okay here is the link I had found last night.  

[http://support.mozilla.com/tiki-view_forum_thread.php?locale=tr&forumId=1&comments_threshold=0&comments_parentId=212585&comments_offset=0&comments_per_page=20&thread_style=commentStyle_plain](http://support.mozilla.com/tiki-view_forum_thread.php?locale=tr&forumId=1&comments_threshold=0&comments_parentId=212585&comments_offset=0&comments_per_page=20&thread_style=commentStyle_plain)

It doesnt specifically address linux builds, but I am not sure that the problem I have is actually linux in nature...

Here is an example of the warnings I am seeing in the Firefox Error console.

Warning: Expected declaration but found '*'.  Skipped to next declaration.
Source File: [http://support.mozilla.com/minify.php/css_styles_mozcommon;css_styles_mozfr](http://support.mozilla.com/minify.php/css_styles_mozcommon;css_styles_mozfr)
Line: 1

He is definitively not talking about Linux. He doesn't mention any closed ports, but he does talk about the firewall blocking Firefox access. I think he is referring to permissions, since some Windows firewalls like Comodo also have some sort of intrusion detection system, which prevents an application from modifying some files that could compromise the system. When Firefox update itself, these intrusion detection systems could not recognize the application and prevent it from writing to the disk. I guess it is possible to induce a crash with such a protection tool. Keep in mind that this has nothing to do with network access and ports, but with additional functionality of some Windows firewalls and all-in-one security solutions.

Your Linux box is not affected by this.

---

### Post by hyper_ch on 2009-04-07
> **Daremo_06 said:**
> Through a router and then onto local cable internet.
Then configure the router. No need to mess with your linux box.

> **Daremo_06 said:**
> instead I am trying to resolve an issue between firefox and flash/javascripts which causes firefox to crash as if I killed it. 
That's a firefox issue and not a firewall one.

---

### Post by cegpope on 2009-04-08
I am also having a firefox/flash issue that is somehow related to firestarter/iptables/a zoom dsl router.

When my laptop is connected to the net at home via a Linksys router or at my mom's via a Belkin router everything is fine, but when my fiancee takes the laptop away to college and is connecting via a Zoom DSL modem-router unit, sites such as Facebook, Hulu, etc... cause Firefox to freeze and crash. However, if I run firestarter and stop the firewall (so that iptables -nL returns Accept policies) the sites work fine.


I suspect my problem and his are related.

---

### Post by DJonsson2008 on 2009-04-28
My experience is that Firestarter did cause problems with my local peer-to-peer connections. It seems what I need is a good IP Traffic
monitor coupled with UFW and perhaps gufw.

Where can I find a better IP Traffic monitor than Firestarter.

---

### Post by lovinglinux on 2009-04-28
> **DJonsson2008 said:**
> Where can I find a better IP Traffic monitor than Firestarter.

To install

```
sudo apt-get install iptstate
```

```
sudo apt-get install iptrfaf
```

To use

```
sudo iptstate
```

```
sudo iptraf
```

To monitor blocked connections check this:

[http://ubuntuforums.org/showpost.php?p=7156014&postcount=13](http://ubuntuforums.org/showpost.php?p=7156014&postcount=13)

---

### Post by DJonsson2008 on 2009-04-28
Thanks for the IPTraf link, its very useful.

In the meantime I used gnome-nettool aka Gnome Network Tool
to scan my local machines ports, and used ufw to open the 
needed ports for samba. The gnome-nettool is not as 
comprehensive as iptraf but in this instance did the job.

I tried gufw again, but do not find it all that smooth,
it seems the best combination may be a good ip traffic
monitor and simply using command line ufw, because I always
suspect Firestarter and gufw may be making opaque assumptions 
somewhere in their default settings. As well Gufw did not display
existing allowances that I knew were made earlier with ufw. From my experience both Firestarter and Gufw have issues.

---

### Post by amandaG on 2009-04-28
RE: Daremo's message: "If I didn't specifically download Firestarter or any other firewall program, then there is none in a normal x64 8.10 correct?"

Actually Ubuntu already comes with the firewall called iptables. I'm looking around for a comprehensive manual for it so that I can modify and add rules with confidence. :)

---

### Post by lovinglinux on 2009-04-28
> **amandaG said:**
> Actually Ubuntu already comes with the firewall called iptables. I'm looking around for a comprehensive manual for it so that I can modify and add rules with confidence. :)

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)
[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

BTW, to reply to a specific post, use the quote button on the bottom right corner. It's much easier and it will include a link to the original post automatically.

---

