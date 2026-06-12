---
title: "clicking on email url doesn't open browser."
date: 2009-06-05
forum: General Help
---

### Post by dluzius on 2009-06-05
New to ubuntu, only been using it for 5 days now, and already I love it.
But one small thing, in Windows, if I click on an URL in an email, my browser would open automatically and take me there.
But ubuntu won't do this, even when the email software is Thunderbird and my default browser is Firefox.
Have I missed a setting somewhere?
   Dave

---

### Post by QIII on 2009-06-05
Open a new tab in Firefox and type 

about:config.


In the filters box, type

network.protocol-handler.app.apt

Let me know what it says in the value column.

---

### Post by dluzius on 2009-06-06
OK, did as you suggested, and value column says
/usr/bin/apturl

now what??

---

### Post by QIII on 2009-06-06
Now . . .

I try to find a way to get you up and running other than by messing with your Thunderbird prefs.js file.

It may come to that, but I hate to make you mess with editing a fairly critical file.

---

### Post by dluzius on 2009-06-06
Sounds good, hope you are able to help me with this.

---

### Post by QIII on 2009-06-06
Please don't be offended, but I am going to go back to a basic question and start from there.  I'm really surprised this is not working for you.

Could you go to System -> Preferences -> Preferred Applications and click the Internet tab to be sure that Firefox is your default?

---

### Post by colau on 2009-06-06
> **dluzius said:**
> New to ubuntu, only been using it for 5 days now, and already I love it.
But one small thing, in Windows, if I click on an URL in an email, my browser would open automatically and take me there.
But ubuntu won't do this, even when the email software is Thunderbird and my default browser is Firefox.
Have I missed a setting somewhere?
   Dave
Is firefox your default browser?
What happens if you click a link in mail?

---

### Post by QIII on 2009-06-06
I asked dluzius to check that.  I was wondering.

Anyway... If Firefox is the default browser as I described above, there is something that might be worthwhile testing, just to see what happens (OK, what I want to do is see if a reinstall of Thunderbird is needed, which I hope isn't the case.)

Go to Applications -> Add/Remove ->  Internet.

Scroll down to find Epiphany web browser and select it to install.

When you get it installed, go to System -> Preferences -> Preferred Applications and select Epiphany as your default browser.  You can always change it back to Firefox later.

See if your links in Thunderbird will open in Epiphany.

---

