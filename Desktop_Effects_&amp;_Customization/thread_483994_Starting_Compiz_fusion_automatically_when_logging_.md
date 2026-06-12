---
title: "Starting Compiz fusion automatically when logging in"
date: 2007-06-25
forum: Desktop Effects &amp; Customization
---

### Post by MonsterDuc on 2007-06-25
How can I avoid to manually start Compiz fusion when I log in to my box?  Would be nice if could avoid the atl+f2 then compiz --replace combination...

Searched the forum but found nothing so far...

Monster

---

### Post by Waappu on 2007-06-25
Go to System > Preferences > Sessions
then to the Startup Programs tab.
Click the Add or New button and type in ```
compiz --replace
```

---

### Post by ivesjd on 2007-06-25
What about for the people that can't boot like that? I.E. it boots to a black screen with only a cursor.

---

### Post by Waappu on 2007-06-25
> **ivesjd said:**
> What about for the people that can't boot like that? I.E. it boots to a black screen with only a cursor.

Hi

Sorry, can't quite understand what you mean. Could you please give more information about how you boot

---

### Post by ivesjd on 2007-06-25
> **Waappu said:**
> Hi

Sorry, can't quite understand what you mean. Could you please give more information about how you boot

When I add either "compiz --replace   and in another emerald --replace &" or "comiz --replace -c emerald &" to the start-up menu. It boots up, lets me log in, then I get a black screen with my cursor. I can sometimes restart X and everything is fine. Usually when I restart X though, I get a problem with the top and bottom panels. I can boot into standard metacity and then run the command "comiz --replace -c emerald &" and it switches to compiz just fine. It is quite frustrating.

---

### Post by MonsterDuc on 2007-06-25
Worked like a charm!  Thanks!

---

### Post by Waappu on 2007-06-26
> **ivesjd said:**
> When I add either "compiz --replace   and in another emerald --replace &" or "comiz --replace -c emerald &" to the start-up menu. It boots up, lets me log in, then I get a black screen with my cursor. I can sometimes restart X and everything is fine. Usually when I restart X though, I get a problem with the top and bottom panels. I can boot into standard metacity and then run the command "comiz --replace -c emerald &" and it switches to compiz just fine. It is quite frustrating.

Hi

Try to create startup script.

Type in terminal ```
sudo gedit /usr/local/bin/compiz-start
```

Then paste these lines to file and save```
#!/bin/bash
sleep 30
compiz --replace -c emerald &

```
make script excutable
```
sudo chmod +x /usr/local/bin/compiz-start
```
then add ```
compiz-start
```to startup programs

---

### Post by ivesjd on 2007-06-26
I was really hoping that would work. Although I didnt expect much since I had tried almost the same thing. It just boots into metacity though.

---

### Post by Waappu on 2007-06-26
> **ivesjd said:**
> I was really hoping that would work. Although I didnt expect much since I had tried almost the same thing. It just boots into metacity though.

Hi

That script should start compiz with 30 sec delay giving time to other apps to load first.

---

### Post by Waappu on 2007-06-26
Hi

There was typo in my post. Command in start up script should be compiz --replace -c emerald &.

---

### Post by ivesjd on 2007-06-26
Wow, I missed the typo. I'm gonna try this again. /me crosses fingers

---

### Post by ivesjd on 2007-06-26
Still not working. This is quite strange.

---

### Post by Waappu on 2007-06-26
Hi

I forgot to say that you need make script excutable :(

type in terminal
```
sudo chmod +x /usr/local/bin/compiz-start
```

---

### Post by ivesjd on 2007-06-26
I should have caught that one as well :) and I found this written byTreviño himself over on the Open Compositing forums .
>     * In few GNOME configurations, if you put compiz --replace on sessions, when gnome starts compiz is loaded only after some seconds (minutes) of freeze, while the gnome splash screen is shown... I can't understand why!
So at least he knows it.

The link to that is [http://forums.opencompositing.org/viewtopic.php?f=48&t=729&p=7198&hilit=#p7198](http://forums.opencompositing.org/viewtopic.php?f=48&t=729&p=7198&hilit=#p7198)

Gonna try making it executible now :P

---

### Post by ivesjd on 2007-06-26
IT WORKS! Thank you so much. Now I'm just gonna mess with the time abit to get it perfect :)

---

### Post by 5735guy on 2008-01-10
Excellent Thankyou, having to run replace each time I booted was a little tedious. HAPPY DAYS :):):):)

---

