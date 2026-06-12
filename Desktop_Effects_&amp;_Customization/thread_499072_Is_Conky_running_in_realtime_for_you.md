---
title: "Is Conky running in realtime for you ?"
date: 2007-07-12
forum: Desktop Effects &amp; Customization
---

### Post by ukripper on 2007-07-12
Is Conky running in realtime for you or receiving some ms/secs delays on your desktop to get current status?

For me it is taking few mili secs to display current status

---

### Post by Happy_Man on 2007-07-12
I am on Kubuntu, so I use the amazing SuperKaramba utility. And yes, there is a perceptible lag on Conky, although I think that can be fixed by editing some interval or other.... sorry, I read this a few months ago, and the value does not immediately jump to mind.

---

### Post by notwen on 2007-07-12
Good thing for me, these precious milli-seconds aren't too important, lol.

---

### Post by Espreon on 2007-07-12
What is Conky?

---

### Post by smbm on 2007-07-12
Mine takes a few secs (2 I think) but only because I have it set up to do this.

---

### Post by Nythain on 2007-07-12
there's an option in the .conkyrc:
```

# Update interval in seconds
update_interval 1.0

```
not sure if dropping that down to 0.0 or just 0 will make it "real time" or if you are always stuck witha few miliseconds of processing time

---

### Post by ukripper on 2007-07-12
> **Nythain said:**
> there's an option in the .conkyrc:
[CODE]
# Update interval in seconds
update_interval 1.0
[CODE]
not sure if dropping that down to 0.0 or just 0 will make it "real time" or if you are always stuck witha few miliseconds of processing time

I am going to try once I get home. lets c if conky could compete gkrellm or superkaramba.

---

### Post by Nythain on 2007-07-12
as far as im concerned, conky blows gkrellm out of the water, but superkaramba still have some features that conky just cant do, but conky is lighter, and runs without major dependencies on either desktops libraries so its #1 in my book (nothing sucks more than junkin up a perfectly minimal fluxbox install with half of gnome and kde)

---

### Post by ukripper on 2007-07-12
> **Nythain said:**
> as far as im concerned, conky blows gkrellm out of the water, but superkaramba still have some features that conky just cant do, but conky is lighter, and runs without major dependencies on either desktops libraries so its #1 in my book (nothing sucks more than junkin up a perfectly minimal fluxbox install with half of gnome and kde)

Conky is fairly good, my only concern is I need information in realtime without sacrificing major resources. Conky does job very well for me though including network graphs and outbound and inbounds which i think gkrellm lacks big time and not intuitive at all in gkrellm.

---

### Post by ukripper on 2007-07-12
good news is I managed to bring conky in realtime but it takes alot of processsing so i just changed interval  to .80 and now it seems nearest to what i was trying to achieve. thanks

---

### Post by [Alsharifi] on 2007-09-04
> **Espreon said:**
> What is Conky?


newb question, i hear it all the time...what is conky?

---

### Post by ukripper on 2007-09-04
> **'[Alsharifi] said:**
> newb question, i hear it all the time...what is conky?

Conky is lightweight system monitor with loads of customization -

Here is link 
[http://conky.sourceforge.net/](http://conky.sourceforge.net/)

---

### Post by [Alsharifi] on 2007-09-04
would u prefer it over gkrellm?

Do u need special hardware for it to read ur computer Temp?

---

### Post by ukripper on 2007-09-04
> **'[Alsharifi] said:**
> would u prefer it over gkrellm?

Do u need special hardware for it to read ur computer Temp?

Things you can do with conky gkreallm doesn't even come near it. try it and find out yourself.

you need to install hddtemp and add  it to your conkyrc script. 

Here you can find out alot of customization for conky, link as below-
[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

Find little howto for Conky as below -
[http://ubuntuforums.org/showthread.php?t=205865&highlight=how+to+install+conky](http://ubuntuforums.org/showthread.php?t=205865&highlight=how+to+install+conky)

---

### Post by bimmerd00d on 2007-09-04
man you guys have that intereval low!  I have mine set to 3.0 and i'm dead happy.  It updates enough for me without using much CPU powah

---

### Post by ukripper on 2007-09-04
> **bimmerd00d said:**
> man you guys have that intereval low!  I have mine set to 3.0 and i'm dead happy.  It updates enough for me without using much CPU powah

I have set it to .8 works like realtime.

---

