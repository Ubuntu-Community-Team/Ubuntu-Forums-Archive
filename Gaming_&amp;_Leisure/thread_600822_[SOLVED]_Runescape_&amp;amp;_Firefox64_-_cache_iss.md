---
title: "[SOLVED] Runescape &amp;amp; Firefox64 - cache issue"
date: 2007-11-02
forum: Gaming &amp; Leisure
---

### Post by crjackson on 2007-11-02
I have Gutsy 64 with java working well.  I can play runescap with firefox64 if I scroll to the bottom of the page and seleced "no sighed app" or something like that.

If I try to play at default settings, I get an error telling me that it can't create a cache directory and I should create a /rscache .

I did that and it didn't work.

I installed the 32 bit firefox with flash/java and I got the same error the first time.  I closed the borwser and tried agan.  It worked.

I checked my home folder and found something like .jagex_cache_32 or some such.

I've tried various ways (launching as root from terminal and making various directories).  Nothing worked.  It doesn't seem to be a java or flash problem  at all.  It seems to be a directory issue.

Can anyone make this work under firefox64?

---

### Post by crjackson on 2007-11-02
No one knows?

---

### Post by Vadi on 2007-11-02
I don't use firefox64, but I'll try and help you out.

Could you make a screenshot or something of the error messages? They were somewhat unclear.

---

### Post by damvcoool on 2007-11-02
use IcedTea java7 and use the unsigned java applet. that's what i do.

---

### Post by crjackson on 2007-11-02
> **Vadi said:**
> I don't use firefox64, but I'll try and help you out.

Could you make a screenshot or something of the error messages? They were somewhat unclear.

I'm at work right now.  Thanks for your help, I'll do this in the morning and maybe you can help me nail this down.

---

### Post by crjackson on 2007-11-03
> **Vadi said:**
> I don't use firefox64, but I'll try and help you out.

Could you make a screenshot or something of the error messages? They were somewhat unclear.

Here's the screen shot...

---

### Post by Vadi on 2007-11-03
That's really weird. Did you fiddle with your java cache settings any?

---

### Post by crjackson on 2007-11-03
> **Vadi said:**
> That's really weird. Did you fiddle with your java cache settings any?

I didn't know there were java cache settings to fiddle with to begin with.

---

### Post by Vadi on 2007-11-03
:/

Try asking on launchpad.net.

---

### Post by mig5 on 2007-11-04
Make a folder in /home/[username]/ called .file_store_32

---

### Post by crjackson on 2007-11-04
> **mig5 said:**
> Make a folder in /home/[username]/ called .file_store_32

**Didn't work**

---

### Post by mig5 on 2007-11-05
Did you create the folder as root? Or as your normal user? (it should have been your normal user).
Try creating a sub directory underneath /home/[username]/.file_store_32 called runescape, so the file structure would be /home/[username]/.file_store_32/runescape/
What add-ons do you have installed in your firefox? (tools -> add-ons)?
Which version of Java do you have installed?
When you try to load the signed applet, do you get a security warning asking you whether you wish to run the applet?

---

### Post by crjackson on 2007-11-05
> **mig5 said:**
> Did you create the folder as root? Or as your normal user? (it should have been your normal user).
Try creating a sub directory underneath /home/[username]/.file_store_32 called runescape, so the file structure would be /home/[username]/.file_store_32/runescape/
What add-ons do you have installed in your firefox? (tools -> add-ons)?
Which version of Java do you have installed?
When you try to load the signed applet, do you get a security warning asking you whether you wish to run the applet?

Okay, created the directories as above.  I get this error (see screen shot).

I have the add-ons above,  Only thing I've added from default install is a Firefox theme. I have IcedTea Java 7, all tests perfectly on the sun Java website.

---

### Post by Waistless on 2007-11-09
I'm having the same troubles as the rest of you, here's some output from the  terminal when trying to load up runescape with cache, might be useful...

```

GCJ PLUGIN: thread 0x6195b0: NP_Initialize
GCJ PLUGIN: thread 0x6195b0: plugin_test_appletviewer
GCJ PLUGIN: thread 0x6195b0: plugin_test_appletviewer return
GCJ PLUGIN: thread 0x6195b0: NP_Initialize: using /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/../../bin/pluginappletviewer
GCJ PLUGIN: thread 0x6195b0: NP_Initialize return
GCJ PLUGIN: thread 0x6195b0: GCJ_New
GCJ PLUGIN: thread 0x6195b0: plugin_data_new
GCJ PLUGIN: thread 0x6195b0: plugin_data_new return
GCJ PLUGIN: thread 0x6195b0: plugin_get_documentbase
GCJ PLUGIN: thread 0x6195b0: plugin_get_documentbase return
GCJ PLUGIN: thread 0x6195b0: GCJ_New: creating input fifo: /home/trystan/.gcjwebplugin/gcj-instance-10415-0-appletviewer-to-plugin
GCJ PLUGIN: thread 0x6195b0: GCJ_New: created input fifo: /home/trystan/.gcjwebplugin/gcj-instance-10415-0-appletviewer-to-plugin
GCJ PLUGIN: thread 0x6195b0: GCJ_New: creating output fifo: /home/trystan/.gcjwebplugin/gcj-instance-10415-0-plugin-to-appletviewer
GCJ PLUGIN: thread 0x6195b0: GCJ_New: created output fifo: /home/trystan/.gcjwebplugin/gcj-instance-10415-0-plugin-to-appletviewer
GCJ PLUGIN: thread 0x6195b0: plugin_start_appletviewer
GCJ PLUGIN: thread 0x6195b0: plugin_start_appletviewer return
GCJ PLUGIN: thread 0x6195b0: GCJ_New: got confirmation that appletviewer is running.
  PIPE: appletviewer wrote: runningGCJ PLUGIN: thread 0x6195b0: plugin_create_applet_tag

GCJ PLUGIN: thread 0x6195b0: plugin_create_applet_tag return
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: instance-10415-0
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: tag http://au2.runescape.com/l0,p0,j1 <EMBED ARCHIVE="loader1214529843.jar" CODE="loader.class" HEIGHT="503" WIDTH="765" ><PARAM NAME="name" VALUE="app"><PARAM NAME="mayscript" VALUE=""><PARAM NAME="cabbase" VALUE="loader1685118758.cab"><PARAM NAME="worldid" VALUE="108"><PARAM NAME="members" VALUE="0"><PARAM NAME="modewhat" VALUE="0"><PARAM NAME="modewhere" VALUE="0"><PARAM NAME="lowmem" VALUE="0"><PARAM NAME="lang" VALUE="0"><PARAM NAME="plug" VALUE="0"><PARAM NAME="js" VALUE="1"><PARAM NAME="game" VALUE="0"></EMBED>
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer return
  PIPE: appletviewer read: instance-10415-0GCJ PLUGIN: thread 0x6195b0: GCJ_New return

GCJ PLUGIN: thread 0x6195b0: NP_GetValue
GCJ PLUGIN: thread 0x6195b0: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x6195b0: NP_GetValue return
GCJ PLUGIN: thread 0x6195b0: GCJ_GetValue
GCJ PLUGIN: thread 0x6195b0: GCJ_GetValue: returning TRUE for NeedsXEmbed.
GCJ PLUGIN: thread 0x6195b0: GCJ_GetValue return
  PIPE: appletviewer read: tag http://au2.runescape.com/l0,p0,j1 <EMBED ARCHIVE="loader1214529843.jar" CODE="loader.class" HEIGHT="503" WIDTH="765" ><PARAM NAME="name" VALUE="app"><PARAM NAME="mayscript" VALUE=""><PARAM NAME="cabbase" VALUE="loader1685118758.cab"><PARAM NAME="worldid" VALUE="108"><PARAM NAME="members" VALUE="0"><PARAM NAME="modewhat" VALUE="0"><PARAM NAME="modewhere" VALUE="0"><PARAM NAME="lowmem" VALUE="0"><PARAM NAME="lang" VALUE="0"><PARAM NAME="plug" VALUE="0"><PARAM NAME="js" VALUE="1"><PARAM NAME="game" VALUE="0"></EMBED>
GCJ PLUGIN: thread 0x6195b0: GCJ_SetWindow
GCJ PLUGIN: thread 0x6195b0: GCJ_SetWindow: setting window.
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: instance-10415-0
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: handle 69210598
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6195b0: GCJ_SetWindow return
GCJ PLUGIN: thread 0x6195b0: GCJ_SetWindow
GCJ PLUGIN: thread 0x6195b0: GCJ_SetWindow: window already exists.
GCJ PLUGIN: thread 0x6195b0: GCJ_SetWindow: window width changed.
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: instance-10415-0
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: width 765
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6195b0: GCJ_SetWindow: window height changed.
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: instance-10415-0
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: height 503
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6195b0: GCJ_SetWindow return
GCJ PLUGIN: thread 0x6195b0: GCJ_SetWindow
GCJ PLUGIN: thread 0x6195b0: GCJ_SetWindow: window already exists.
GCJ PLUGIN: thread 0x6195b0: GCJ_SetWindow return
  PIPE: appletviewer read: instance-10415-0
  PIPE: appletviewer read: handle 69210598
Warning: <param name=... value=...> tag requires name attribute.
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback: setting status starting applet...
  PIPE: plugin read: status starting applet...
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback return
  PIPE: appletviewer wrote: status starting applet...
  PIPE: appletviewer read: instance-10415-0
  PIPE: appletviewer read: width 765
  PIPE: appletviewer read: instance-10415-0
  PIPE: appletviewer read: height 503
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback: setting status Applet loaded.
  PIPE: plugin read: status Applet loaded.
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback return
  PIPE: appletviewer wrote: status Applet loaded.
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback: setting status Applet initialized.
  PIPE: plugin read: status Applet initialized.
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback return
  PIPE: appletviewer wrote: status Applet initialized.
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback: **opening URL http://au2.runescape.com/error_loader_nocache.ws**
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback: URL target _self

...

```

---

### Post by crjackson on 2007-11-09
> **Waistless said:**
> I'm having the same troubles as the rest of you, here's some output from the  terminal when trying to load up runescape with cache, might be useful...

```

GCJ PLUGIN: thread 0x6195b0: NP_Initialize
GCJ PLUGIN: thread 0x6195b0: plugin_test_appletviewer
GCJ PLUGIN: thread 0x6195b0: plugin_test_appletviewer return
GCJ PLUGIN: thread 0x6195b0: NP_Initialize: using /usr/lib/jvm/java-7-icedtea/jre/lib/amd64/../../bin/pluginappletviewer
GCJ PLUGIN: thread 0x6195b0: NP_Initialize return
GCJ PLUGIN: thread 0x6195b0: GCJ_New
GCJ PLUGIN: thread 0x6195b0: plugin_data_new
GCJ PLUGIN: thread 0x6195b0: plugin_data_new return
GCJ PLUGIN: thread 0x6195b0: plugin_get_documentbase
GCJ PLUGIN: thread 0x6195b0: plugin_get_documentbase return
GCJ PLUGIN: thread 0x6195b0: GCJ_New: creating input fifo: /home/trystan/.gcjwebplugin/gcj-instance-10415-0-appletviewer-to-plugin
GCJ PLUGIN: thread 0x6195b0: GCJ_New: created input fifo: /home/trystan/.gcjwebplugin/gcj-instance-10415-0-appletviewer-to-plugin
GCJ PLUGIN: thread 0x6195b0: GCJ_New: creating output fifo: /home/trystan/.gcjwebplugin/gcj-instance-10415-0-plugin-to-appletviewer
GCJ PLUGIN: thread 0x6195b0: GCJ_New: created output fifo: /home/trystan/.gcjwebplugin/gcj-instance-10415-0-plugin-to-appletviewer
GCJ PLUGIN: thread 0x6195b0: plugin_start_appletviewer
GCJ PLUGIN: thread 0x6195b0: plugin_start_appletviewer return
GCJ PLUGIN: thread 0x6195b0: GCJ_New: got confirmation that appletviewer is running.
  PIPE: appletviewer wrote: runningGCJ PLUGIN: thread 0x6195b0: plugin_create_applet_tag

GCJ PLUGIN: thread 0x6195b0: plugin_create_applet_tag return
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: instance-10415-0
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: tag http://au2.runescape.com/l0,p0,j1 <EMBED ARCHIVE="loader1214529843.jar" CODE="loader.class" HEIGHT="503" WIDTH="765" ><PARAM NAME="name" VALUE="app"><PARAM NAME="mayscript" VALUE=""><PARAM NAME="cabbase" VALUE="loader1685118758.cab"><PARAM NAME="worldid" VALUE="108"><PARAM NAME="members" VALUE="0"><PARAM NAME="modewhat" VALUE="0"><PARAM NAME="modewhere" VALUE="0"><PARAM NAME="lowmem" VALUE="0"><PARAM NAME="lang" VALUE="0"><PARAM NAME="plug" VALUE="0"><PARAM NAME="js" VALUE="1"><PARAM NAME="game" VALUE="0"></EMBED>
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer return
  PIPE: appletviewer read: instance-10415-0GCJ PLUGIN: thread 0x6195b0: GCJ_New return

GCJ PLUGIN: thread 0x6195b0: NP_GetValue
GCJ PLUGIN: thread 0x6195b0: NP_GetValue: returning plugin description.
GCJ PLUGIN: thread 0x6195b0: NP_GetValue return
GCJ PLUGIN: thread 0x6195b0: GCJ_GetValue
GCJ PLUGIN: thread 0x6195b0: GCJ_GetValue: returning TRUE for NeedsXEmbed.
GCJ PLUGIN: thread 0x6195b0: GCJ_GetValue return
  PIPE: appletviewer read: tag http://au2.runescape.com/l0,p0,j1 <EMBED ARCHIVE="loader1214529843.jar" CODE="loader.class" HEIGHT="503" WIDTH="765" ><PARAM NAME="name" VALUE="app"><PARAM NAME="mayscript" VALUE=""><PARAM NAME="cabbase" VALUE="loader1685118758.cab"><PARAM NAME="worldid" VALUE="108"><PARAM NAME="members" VALUE="0"><PARAM NAME="modewhat" VALUE="0"><PARAM NAME="modewhere" VALUE="0"><PARAM NAME="lowmem" VALUE="0"><PARAM NAME="lang" VALUE="0"><PARAM NAME="plug" VALUE="0"><PARAM NAME="js" VALUE="1"><PARAM NAME="game" VALUE="0"></EMBED>
GCJ PLUGIN: thread 0x6195b0: GCJ_SetWindow
GCJ PLUGIN: thread 0x6195b0: GCJ_SetWindow: setting window.
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: instance-10415-0
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: handle 69210598
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6195b0: GCJ_SetWindow return
GCJ PLUGIN: thread 0x6195b0: GCJ_SetWindow
GCJ PLUGIN: thread 0x6195b0: GCJ_SetWindow: window already exists.
GCJ PLUGIN: thread 0x6195b0: GCJ_SetWindow: window width changed.
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: instance-10415-0
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: width 765
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6195b0: GCJ_SetWindow: window height changed.
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: instance-10415-0
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer
  PIPE: plugin wrote: height 503
GCJ PLUGIN: thread 0x6195b0: plugin_send_message_to_appletviewer return
GCJ PLUGIN: thread 0x6195b0: GCJ_SetWindow return
GCJ PLUGIN: thread 0x6195b0: GCJ_SetWindow
GCJ PLUGIN: thread 0x6195b0: GCJ_SetWindow: window already exists.
GCJ PLUGIN: thread 0x6195b0: GCJ_SetWindow return
  PIPE: appletviewer read: instance-10415-0
  PIPE: appletviewer read: handle 69210598
Warning: <param name=... value=...> tag requires name attribute.
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback: setting status starting applet...
  PIPE: plugin read: status starting applet...
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback return
  PIPE: appletviewer wrote: status starting applet...
  PIPE: appletviewer read: instance-10415-0
  PIPE: appletviewer read: width 765
  PIPE: appletviewer read: instance-10415-0
  PIPE: appletviewer read: height 503
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback: setting status Applet loaded.
  PIPE: plugin read: status Applet loaded.
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback return
  PIPE: appletviewer wrote: status Applet loaded.
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback: setting status Applet initialized.
  PIPE: plugin read: status Applet initialized.
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback return
  PIPE: appletviewer wrote: status Applet initialized.
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback: **opening URL http://au2.runescape.com/error_loader_nocache.ws**
GCJ PLUGIN: thread 0x6195b0: plugin_in_pipe_callback: URL target _self

...

```

Thanks, I still haven't figured it out...

---

### Post by jazz452 on 2007-11-10
all you have to do is use konqueror 64 works no problem.But remember once you have set your home page. Select,settings,save view profile (web browsing).Just install java 6 bin
Konqueror takes slightly longer to load but once up and running seems to be fastest web browser.You can install from synaptics also install konq pluggins

---

### Post by crjackson on 2007-11-12
> **jazz452 said:**
> all you have to do is use konqueror 64 works no problem.But remember once you have set your home page. Select,settings,save view profile (web browsing).Just install java 6 bin
Konqueror takes slightly longer to load but once up and running seems to be fastest web browser.You can install from synaptics also install konq pluggins

I can run it by installing Firefox 32 bit, and by selecting not to use the mode that caches the files.  The point is to get it working under Firefox64.  I have 2 machines that the kids use Firefox 32 on for playing, but I want to get it working under 64-bit FF.

---

### Post by mig5 on 2007-11-14
You still haven't answered this question:
> 
When you try to load the signed applet, do you get a security warning asking you whether you wish to run the applet?


If the answer to it is no then the problem might be related to your java security settings.  I'm not familiar with the Java version that you are using, but with Sun JRE 1.6 the security policy files are stored in /etc/java-6-sun/security and there is also a control panel with some basic setting options in /usr/lib/jvm/java-6-sun-1.6.0.03/jre/bin/jcontrol .

---

### Post by crjackson on 2007-11-14
> **mig5 said:**
> You still haven't answered this question:


If the answer to it is no then the problem might be related to your java security settings.  I'm not familiar with the Java version that you are using, but with Sun JRE 1.6 the security policy files are stored in /etc/java-6-sun/security and there is also a control panel with some basic setting options in /usr/lib/jvm/java-6-sun-1.6.0.03/jre/bin/jcontrol .

No I don't get any warnings.

---

### Post by Zelphien on 2007-11-14
I have this problem too. Its your java settings or whatever. It isnt Firefox. I thought it was FireFox so i got another web browser from the Synaptic of Ubuntu Gusty. It still doesn't work I solved the problem:

When you are at the page to select High Detail or Low Detail, scroll all the way down where it has the Java Selections. Click on the arrow and click on the Unsigned Java Option and click High Detail button under that(not the real Detail buttons). It should work. Works for me now.

---

### Post by jazz452 on 2007-11-17
> **crjackson said:**
> I can run it by installing Firefox 32 bit, and by selecting not to use the mode that caches the files.  The point is to get it working under Firefox64.  I have 2 machines that the kids use Firefox 32 on for playing, but I want to get it working under 64-bit FF.
Thats why i said to use konqueror web browser its 64 bit

---

### Post by jazz452 on 2008-01-30
Now lets start at the beginning java have not got a 64 bit browser plugin.That is why it will never work no matter what u do in firefox. Konqueror doesnt need a plugin because you have to specify the folder where java is.In my case it is in :

 /usr/lib/jvm/java-6-sun-1.6.0.04/bin/java    You do this from java & javascript.
I cant see the point of going to all the trouble of using 64 bit if you are going to install 32 browser.So do yourself a favour install konqueror and all its plugins it is an excellent browser.

---

### Post by crjackson on 2008-01-31
> **jazz452 said:**
> Now lets start at the beginning java have not got a 64 bit browser plugin.That is why it will never work no matter what u do in firefox. Konqueror doesnt need a plugin because you have to specify the folder where java is.In my case it is in :

 /usr/lib/jvm/java-6-sun-1.6.0.04/bin/java    You do this from java & javascript.
I cant see the point of going to all the trouble of using 64 bit if you are going to install 32 browser.So do yourself a favour install konqueror and all its plugins it is an excellent browser.

As you can plainly see I haven't posted in this thread since May last year.  Please stop trying to push konqueror on me I'm not interested.  Just let the thread die...

---

### Post by jazz452 on 2008-01-31
yer but you keep checking it :¬)

---

### Post by linux noooob on 2008-01-31
hmmm i am having the same problem hmmm and dude no one wants to use that browser let it DIE

---

### Post by crjackson on 2008-01-31
> **jazz452 said:**
> yer but you keep checking it :¬)
Have you never heard of a subscription.  It's my thread so it sends me an email every time someone posts here.  Of course I'm going to look at it.:roll:

---

### Post by wyrless2002 on 2008-02-18
I don't know if this helps the situation or worsens it, but, I believe I have a possible answer, but no explanation to back up my theory. (Please feel free to expound on this, It's obvious that I'm not the only one that would benefit from dissecting it.)

I have sun-java5-bin, sun-java5-jre, sun-java5-plugin, sun-java6-bin, sun-java6-jre, sun-java6-plugin, and java-common installed. I _think_ Runescape only needs 6 to work.  (If this combination is redundant, maybe someone could explain why for my benefit.  I have had the experience, once, where the site I was on didn't know what to do with jre6 and I had to go back and reinstall jre5, and stayed with this combination for that reason.)

I also **_HAD_** installed, the icedtea-java7-bin, icedtea-java7-jre, and the icedtea-java7-plugin. **WHEN I REMOVED THE icedtea-java7-plugin**, Runescape worked.

I have done this three times now, after installing and re-installing Ubuntu 7.04 and 7.10 either during the upgrade or after a couple of noob botched configurations on my part, and originally I just took 5 and 7 off all together while I was experimenting to get it to work.
 
In a similar note, I found interesting, that in trying to get Frostwire to work (I would download it, via synaptic, or apt-get, and it would seemingly install, and add app. icons, and when clicked on, or run from the menu, it would do nothing. Even though Limewire worked fine.) It installed and ran flawlessly with icedtea-java7 components installed.  So, my next line of thought was, Runescape won't run in Firefox with icedtea installed, but Frostwire will run on the desktop with it installed, what if I removed just the plugin?

I hope maybe someone can translate what I just said into something useful, and point out any errors or misconceptions in a positive manner.  I will appreciate seeing how everyone else gets on. 
-wyrless2002 a.k.a. wraith_ryder (world 44)

---

### Post by codeslicer on 2008-04-19
Thanks!

---

### Post by Triggerhapp on 2008-04-19
Runescape requires any Sun Java or Microsoft's Java, and sadly, no GNU java yet can get it to run right, which is a shame

---

### Post by Rithmarin on 2008-06-07
I had this problem with firefox and fixed it after I removed the icedtea-gcjwebplugin package. Somehow it was linking that in preference to the sun-java plugin. If you run firefox from a console window, it will spit out a lot of text, some of which will tell you what it is using to try and load runescape...

---

### Post by psylem on 2008-06-28
I've had the same thing happening for a while with the 32 bit version of firefox 3 (after an update Runescape suddenly stopped working, displaying the error message about the cache write problem).

I tried some things based on wyrless2002 post. sun-java plugin wasn't installed, so I installed it. That didn't fix it but once I removed icedtea-gcjwebplugin then it worked perfectly (I also added icedtea-java7-bin, icedtea-java7-jre, but I take it I can probably remove these now). Thanks all for the input folks.

---

### Post by stjohab2 on 2008-07-05
I had problems with cache errors when loading the Runescape but it works great after uninstalling icedtea-gcjwebplugin. Thank you for the information. I did not install icedtea-java7-bin, icedtea-java7-jre, Runscape worked anyway. Thanks again!

---

