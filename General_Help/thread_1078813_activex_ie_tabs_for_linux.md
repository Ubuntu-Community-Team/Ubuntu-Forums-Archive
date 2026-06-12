---
title: "activex? ie tabs for linux?"
date: 2009-02-23
forum: General Help
---

### Post by BigPanda007 on 2009-02-23
Ive tried several things but am completely lost. I have an online program that needs IE to run. I was able to download ie tabs as an add on in firefox and am able to get it working (in windows). when i use IE in ubuntu and go to the site it allows me to log in but wont display anything except a message that says i need to install active x or enable it. it is enabled under internet options. I cant run firefox in ubuntu with this program cause ie tabs doesnt work. what can i do? the website is [www.toolkitcma.com](www.toolkitcma.com) 

my second question is another program that i have and am using wine. this program also uses IE and when i try to use it i get the message "run time error 429: activex component cant create object." all out of ideas

TIA for any help.


~P

---

### Post by Therion on 2009-02-23
If the site absolutely requires ActiveX (meaning using something like User Agent Switcher will not work) it means you have no choice but to use IE to access the website.  

Still, I guess it's worth a shot.  Get UAS here:

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

Now if that's the case then, meaning the site absolutely *requires* that you be using IE to access their page, I'd be asking myself WHY does this website require that I be using IE?  
I can think of a few reasons and none of them are good.  

I'd also be contacting them via email or phone to let them know why I won't be doing business with them.

---

### Post by mb_webguy on 2009-02-23
I don't think the IE Tab extension in Firefox works in Linux.

The only way to view a site that requires ActiveX is to use IE, and the best way to do that (short of actually running Windows either in a dual boot or a VM) is to use Wine and IEs4Linux.  Make sure you have the most recent version of Wine by adding the [WineHQ repository]("http://www.winehq.org/download/deb"), then download and install the [IEs4Linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page") script to install IE.

---

### Post by BigPanda007 on 2009-02-23
Therion-the user agent switcher worked. thanks..but now it says my computer is vista (and i do have vista on the other boot) and wants to download a file for vista. however i did download the file for s & giggles and like i thought couldnt open it in ubuntu.  

the website is a real estate tool that i use for market analysis and once i locate properties it downloads them as a zip to the computer and then the program opens the zip and takes all the info of the properties. not a personal fan of the program but my hands are tied so im doing what i can on my end.


mb_webguy- i do have wine (but am new to it) and ie4 is installed (actually i have ie6 running) for i just double click on the ie icon and it opens there nothing special i should do to make activex work right?

i just put win and ie on the other day so im not to familiar with them on ubuntu. 


thanks guys any more thoughts?

---

### Post by mb_webguy on 2009-02-23
You probably have to install the website's ActiveX plugin, but other than that it should work.

What's the specific website you're trying to use?

---

### Post by BigPanda007 on 2009-02-23
[www.toolkitcma.com](www.toolkitcma.com)


how would i get there specific activex plugin for the site? how would i install in ubuntu?

---

### Post by mb_webguy on 2009-02-23
Running IE under Wine should be the same as running it under Windows, so you shouldn't have to do anything different in terms of installing the ActiveX plugin.

I was hoping to be able to test that site for myself and see if the problem is with the website or your system, but unfortunately it requires a login to get to the juicy bits...

---

### Post by BigPanda007 on 2009-02-23
this may sound like a really stupid question and it probably is...

how do i "open" ie in wine? as mentioned before i have never used wine before and installed it for another program (that i cant get working either) i thought once wine was loaded i could just click on the ie icon and that was it and thats what i have been doing. ie doesnt show up under the wine programs just on the desktop

---

### Post by mb_webguy on 2009-02-23
Do you see it in Applications->Internet?  That's where mine is, but I can't remember whether it was automatically added, or I added it myself.

---

### Post by BigPanda007 on 2009-02-23
no its not there..only an icon on the desktop

---

### Post by mb_webguy on 2009-02-23
Does the icon on the desktop work?  If so, just edit your menu and add a launcher.

---

### Post by BigPanda007 on 2009-02-23
the icon does work on the desktop...


and for s & giggles i did an install of the software (which you dont have to do to do) and now the site actually lets me log on and go into into it. i did re-start my laptop because ie stopped working for some reason and now everything seems fine for the most part. 

i think i might just have to tweak it. some how :/ ? ie seems to be running really slow with the 2 websites i need it for and it locks up sometimes. 

i really appreciate the help well see what i can do for tomorrow.

when i have time tomorrow ill post more and see if i can get anything to help you in the mean time



Thanks again

---

