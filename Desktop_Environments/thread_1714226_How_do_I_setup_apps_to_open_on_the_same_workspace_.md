---
title: "How do I setup apps to open on the same workspace after reboot"
date: 2011-03-25
forum: Desktop Environments
---

### Post by Jonners59 on 2011-03-25
I use the workspaces a lot.  It helps me de clutter my desktop.  A great tool, thanks guys.

One thing that does bug me about it though, is that every time I start my PC or laptop I have to move the auto start apps to the workspace I want them on.  They always kick off in Workspace 1, I want them in specific spaces.

Can I, and if so how do I make this happen, please?

If it is not a feature, can I recommend it for development.

---

### Post by ~Plue on 2011-03-25
take a look at Devilspie
[https://help.ubuntu.com/community/Devilspie](https://help.ubuntu.com/community/Devilspie)

---

### Post by Jonners59 on 2011-03-25
Thanks for this

I have installed and tried setting up, but the apps still load on workspace 1 and not as I want them....  It appears, according to the description and settings be what I am after, but it does not seem to work.

---

### Post by Krytarik on 2011-03-25
Devilspie is for Metacity.

If you are you using Compiz (desktop effects), see this earlier thread:
[http://ubuntuforums.org/showthread.php?t=1713062](http://ubuntuforums.org/showthread.php?t=1713062)

Greetings.

---

### Post by Jonners59 on 2011-03-25
No, that did not work either, though it is not very clear to the uninitiated as to exactly what one is doing.  It is very geekie....  See pic enclosed as to what I did....

---

### Post by Krytarik on 2011-03-25
OMG! :P  Please read my posts again!
And remove the rules you set up.

---

### Post by Jonners59 on 2011-03-25
Deleted as instructed, followed the links again, but as I stated it is all gobbldie gook speak to me.  It means nothing.  I have tried just following the instructions, but I do not understand what it is saying.  Why it can't just say select ap, select workspace, I don't know...

I have done just one this time, just in case it is wrong again.

I want Firefox in Workspace 6 (which I have called "Browser")...  Following the instructions as best I can the enclosed is what I have.

If this is correct then I want:
Evolution in Workspace 4 (named "eMail")
ekiga in Workspace 8 (named "Phones")

If it is wrong, then I'll leave it.  I have more pressing things to do than try and translate this.

---

### Post by Krytarik on 2011-03-25
Ok, this is really not *that* difficult. This time you did at least find the correct list. ;-)

All you need to do now, is to "Grab" the "class" of your already running window, but I know that those of Firefox is simply "Firefox", the others may be accordingly, but *must not be*.

Then specify the desired viewport/workspace, this depends on your workspace setup. 

For example, I have a 2 cols x 2 rows setup. When I want to fix Firefox on my right upper workspace, I need to set "X Viewport" to "2" and "Y Viewport" to "1". Lower left would be: "X Viewport" = "1", "Y Viewport" = "2".

---

### Post by Jonners59 on 2011-03-25
Thankyou for your patience...

OK, I had another go, I have not tested it but you can confirm if it is correct this time.

What I do not understand is, why when you GRAB an app, it states what it is in the little window, but then when you save it it just says "Class=" and you then have top type the app name/ cmd in...? makes no sense.

Anyway, screen shot.

---

### Post by Krytarik on 2011-03-25
> **Jonners59 said:**
> 
OK, I had another go, I have not tested it but you can confirm if it is correct this time.
Looks fine now. Assuming, you have set up your workspaces all in a row.
> **Jonners59 said:**
> What I do not understand is, why when you GRAB an app, it states what it is in the little window, but then when you save it it just says "Class=" and you then have top type the app name/ cmd in...? makes no sense.

Yeah, that's indeed odd, among some other issues regarding those dialogs.

---

### Post by Jonners59 on 2011-03-25
PC froze so had to do a hard reboot.  Did not work!

---

### Post by Krytarik on 2011-03-25
> **Jonners59 said:**
> PC froze so had to do a hard reboot.  Did not work!
Like I said:
> **Krytarik said:**
> Looks fine now. Assuming, you have set up your workspaces all in a row.
Is that really the case? All workspaces lined up horizontally? If not, look back.

---

### Post by Jonners59 on 2011-03-25
Yes, all in a row.  It froze some time after the changes.  I was downloading an op for my mobile when it happened.

I have also tried for the sake of it doing the same on a different machine - the one I am on now and it did the same.  I had to add the ap even though I had grabbed it.

---

