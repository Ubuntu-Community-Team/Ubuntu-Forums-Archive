---
title: "Comcast Voice Mail Checking"
date: 2009-05-31
forum: General Help
---

### Post by Anito on 2009-05-31
I am using kubuntu 9.04, and I recently installed it a few days ago.

 But heres the problem, I log onto my comcast email to check my voicemails online and it wont allow me to.  A error message comes up saying I need a Quicktime plugin.

 But the thing is, there is no quicktime for Linux...........  So what do I do?

---

### Post by Mirge on 2009-05-31
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

```

**Playing Restricted Formats**

  
Follow these steps to play and record most common multimedia formats, including MP3, DVD, Flash, Quicktime, WMA and WMV, including both standalone files and content embedded in web pages. 
 
**Ubuntu 9.04, 8.10, 8.04 and 7.10**

  
**Synaptic**

 
[LIST]
[*]Go to **Applications** &#8594; **Add/Remove...**
[*]Set Show: to **All available applications**
[*]Search for **ubuntu-restricted-extras** and install it. Note that there is also **xubuntu-restricted-extras** (for Xubuntu) and **kubuntu-restricted-extras** (for Kubuntu.)
[/LIST]
Or open the Terminal, and execute the following command: 

[LIST]
[*]sudo apt-get install ubuntu-restricted-extras
[/LIST]
 

```

---

### Post by Anito on 2009-05-31
Its a wav file.     

This didn't work.

---

### Post by lisati on 2009-05-31
I'm mildly curious: you shouldn't need a full quicktime decoder to play a wav file....

---

### Post by zbeekman on 2010-07-27
A different thread found that installing gecko-mediaplayer fixed this.  I'm still unsure exactly which plugin is needed.

This is great and all, and fixes it for firefox, but google chrome is still broken.  Any one have any thoughts?

Here are all the plugins chrome is using:
[http://uppix.net/b/7/8/37e29f9fbe19ff51f38fdd5ef0e28.png](http://uppix.net/b/7/8/37e29f9fbe19ff51f38fdd5ef0e28.png)

These are what firefox is using:
[http://uppix.net/b/7/8/37e29f9fbe19ff51f38fdd5ef0e28.png](http://uppix.net/b/7/8/37e29f9fbe19ff51f38fdd5ef0e28.png)

Does anyone know exactly which firefox plugin is getting this working?  Also, how do I add that to google chrome?

---

