---
title: "Skype rings once, then I get an error &quot;Problem with sound device&quot;"
date: 2006-08-06
forum: Desktop Environments
---

### Post by chloraldo on 2006-08-06
When I try phoning with skype, it rings once and then stops giving this error "Problem with sound device".

I can listen to music and watch films.

I found some threads with similar problems but none of the solutions helped...

What can I do?

---

### Post by avender on 2006-08-06
I'm not sure whether this helps u or not... But it works in my machine.

Just close all the players such as xmms or amarok before starting Skype. Now start the skype and check.

Best Of Luck.

---

### Post by rpalyvoda on 2006-08-06
Otherwise, you could try Skype 1.3 (beta) available from skype.com

It worked for me

---

### Post by Grog140 on 2006-08-06
I am using the beta and I am getting that error. I also get an error when I start up sound recorder to test my mic as well!

---

### Post by rpalyvoda on 2006-08-06
> **Grog140 said:**
> I am using the beta and I am getting that error. I also get an error when I start up sound recorder to test my mic as well!

I think you'he got a problem with alsa configuration. With my still small knowledge of Linux, I would re-install alsa in Synaptic using re-install package option. However, I'm not sure of myself, so you should look for answer in ubuntu documentation...

---

### Post by ozorba on 2006-08-06
> **Grog140 said:**
> I am using the beta and I am getting that error. I also get an error when I start up sound recorder to test my mic as well!

I had the same problem with Skype Beta. In the end I reverted back to the older version.

---

### Post by AllenGG on 2006-08-06
This is a common problem with SKYPE. Several problems may be caused by "ALSA", but are not ALSA's fault. Go to Synaptic. look at "ALSA", use the search utility, under 'description and name', highlight , for example, "ALSA-BASE",  go to "properties", look at "dependencies" and look at "CONFLICTS". You will have to do this with several entries. There will be "conflicts" that must be un-installed. BEWARE ! some packages can remove GNOME. 
For example: "alsa-utils" conflicts with "alsa-base (>1.09b-3)
And I needed "alsamixergui" installed to get a MIC working on an AMD64, 6.06, hope this helps.

---

