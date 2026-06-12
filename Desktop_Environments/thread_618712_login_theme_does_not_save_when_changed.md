---
title: "login theme does not save when changed"
date: 2007-11-20
forum: Desktop Environments
---

### Post by laihafloyd on 2007-11-20
I am trying to change my login theme using the Login Window in the System>Administration menu on Gutsy and it seems to update when I switch themes, but upon closing, the changes are lost and it reverts to the default.  Any ideas?

---

### Post by rax_m on 2007-11-29
hi, are you sure you're selecting the new login theme properly? 

I find the login theme changer confusing to new users, b'cos you can just select on a new theme, but that doesn't change it. If you look carefully, there are radio buttons next to the screenshot preview. You have to select that for the new theme to take effect. 

Cheers

---

### Post by laihafloyd on 2007-11-30
tried it, but still no change (i honestly don't know if i had been clicking the radio button or just highlighting the option before your reply!) 

I also have other strange desktop issues, i.e. when making changes through advanced desktop effects settings, only the first change happens immediately.  any other changes have to wait until the X server is restarted to take effect.  before upgrading to gutsy, i didn't have either of these issues.

---

### Post by TeaSwigger on 2007-12-01
> **laihafloyd said:**
> tried it, but still no change (i honestly don't know if i had been clicking the radio button or just highlighting the option before your reply!) 

I also have other strange desktop issues, i.e. when making changes through advanced desktop effects settings, only the first change happens immediately.  any other changes have to wait until the X server is restarted to take effect.  before upgrading to gutsy, i didn't have either of these issues.

Are you using root priv. to change the login theme?

As for needing to restart the x server to effect advanced effects settings, that may be by design, I honestly don't know. Do those settings work after restarting x?

---

### Post by OldGlory747 on 2008-01-24
Hey,  I'm having a similar problem. Any changes that I make in the System>Administration>Login Window are lost upon closing the Login Window Preferences window. I'm assuming that I somehow lost root permission to write to the configuration file that it saves to. Also, I've searched both google and ubuntu with no luck. Any ideas?

---

### Post by Tenken on 2008-01-24
Ubuntu won't let you open the Login manager without root permissions, so I don't think that's the problem. I had a similar problem when I first tried switching the login theme, when I switched from the default, the "Theme" drop-down switched from  "Selected only" to "Random from selected" so it kept "randomly" picking the default.

---

