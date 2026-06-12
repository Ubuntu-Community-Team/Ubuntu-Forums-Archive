---
title: "Laptop running hot, tired of it."
date: 2009-04-09
forum: General Help
---

### Post by PhoHammer on 2009-04-09
So my laptop runs hot. After a mere 30 minutes of low intensity web browsing,
I have to remove my laptop from my lap, as it feels as though it is burning me.

I have a HP dv6809wm ( 3 GB RAM, AMD  Turion 64 X2 Dual-Core, more specs if you need
them, just ask) and I'll be running at 0-8% CPU and 12% RAM and it kicks on the fan
like it's about to burst into flames. My environment has a temp of about 65-70 degrees F 
so I don't see how that could affect it.

I previously used Vista and didn't have this problem. Is this an ubuntu problem or Linux
in general. Is there a **Linux distro** that will not run this hot? 

The heat feels like it's coming mostly from the HDD, even though I am not writing or 
reading from it. I ran the hddtemp command and its at 48 degrees C, which is pretty
hot for not using it to any extreme extent. And my CPU is running at 54-61 C...

Any ideas on why this is happening?

Oh and it did this in Xubuntu 8.04 and Ubuntu 8.10 (I'm now using 9.04).

---

### Post by irishrm on 2009-04-09
I had the same problem with my laptop.  I changed to puppy Linux and that works perfectly.   Still use xubuntu on my desktop no problem.Irishrm

---

### Post by PhoHammer on 2009-04-10
Yes, I'm thinking of looking into another distro, but puppy didn't push my buttons like 
ubuntu last time I played with it:p. No one knows why ubuntu does this? hmmm... And I 
can't really say that it might be more taxing on my system than a small distro like puppy or 
dsl, because it never even pushes my system before it gets really hot...

---

### Post by Vunutus on 2009-04-10
This is just a guess but it's possible that processor frequency scaling may not be working under Ubuntu for you, causing the CPU to generate more heat (how much more I'm not sure). The same thing happened with my laptop, causing it to generate a bit of excess heat as well as taking battery life.

---

### Post by x C0MMAND0 x on 2009-04-10
Is it actually running hot, or does it just feel like it?

You can install the sensors applet to check. 

```
sudo apt-get install sensors-applet
```

Then restart computer, right click on panel, add to panel and choose hardware sensors monitor.  This will allow you to check the temperature of your computer and see how hot it is actually running.  I am curious to know...

---

### Post by niraj2709 on 2009-04-10
i wonder, somehow my laptop remains relatively cool...
i have just 512 ram, that too on an intel celeron M..

---

### Post by PhoHammer on 2009-04-10
> **x C0MMAND0 x said:**
> Is it actually running hot, or does it just feel like it?

You can install the sensors applet to check. 

```
sudo apt-get install sensors-applet
```Then restart computer, right click on panel, add to panel and choose hardware sensors monitor.  This will allow you to check the temperature of your computer and see how hot it is actually running.  I am curious to know...

I did that:

>  I ran the hddtemp command and its at 48 degrees C, which is pretty
hot for not using it to any extreme extent. And my CPU is running at 54-61 C...And this is after only about 30 minutes of web browsing.

Edit: I give a range for the CPU as it reports 4 different "cores" in the applet.

---

### Post by sonu 1807 on 2009-04-10
AMDs do run a bit hotter ( I have HP dv6000). I dont think 48 C is high for it. 

In console type sudo apt-get install lm-sensors sensors-applet hddtemp then restart

Then righ click on panel and in add to panel you will see hardware sensors monitor. It will constantly tell you about the temp

---

### Post by HermanAB on 2009-04-10
Sounds like an ACPI problem.  Some googling should get your temperature down.

---

### Post by soltanis on 2009-04-10
What is the Advanced Power Management level setting on your HD? When mine is set to 254/255, it runs about as hot as you described; when it's set to 128, it cools down considerably (but I don't leave it there, because my disk suffers from the excessive head parking problem).

---

### Post by PhoHammer on 2009-04-10
> **soltanis said:**
> What is the Advanced Power Management level setting on your HD? When mine is set to 254/255, it runs about as hot as you described; when it's set to 128, it cools down considerably (but I don't leave it there, because my disk suffers from the excessive head parking problem).
 
How do you change these settings? I googled it and the wikipedia page said APM was developed by MS and Intel...would this apply to my laptop with an AMD processor?

---

### Post by mr.thraz on 2009-04-10
i think its the bios shipped with hp.

i cant wait till open sourced bios is ready for prime-time,
then i can test that theory.

---

### Post by soltanis on 2009-04-10
You change it using the program hdparm.

```

sudo hdparm -B 254 /dev/sda

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)

```

On my computer.

---

### Post by Jazzy_Jeff on 2009-04-10
I am running an Acer laptop with an AMD processor and the hottest it gets is around 53 degress celcius under a full load. Around 20 degrees cooler at normal use. Not sure what your problem is.

---

