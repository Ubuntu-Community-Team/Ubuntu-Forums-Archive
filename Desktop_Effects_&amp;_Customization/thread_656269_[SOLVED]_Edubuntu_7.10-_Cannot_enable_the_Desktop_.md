---
title: "[SOLVED] Edubuntu 7.10- Cannot enable the Desktop effect"
date: 2008-01-02
forum: Desktop Effects &amp; Customization
---

### Post by src2206 on 2008-01-02
Hello

I have installed **[SIZE=3][COLOR=Blue]Edubuntu 7.10[/COLOR][/SIZE] **(thank you** ShipIt** for providing it), but I can not enable desktop Effects using [COLOR=DarkRed]**System> Preferences> Appearance> Visual Effects**[/COLOR]. I get the following error messages as posted in the Screen Shots. I tried both **Normal** and **Extra** options, none of the two worked and gave the same error message as follows.

[IMG]http://img141.imageshack.us/img141/6711/screenshotappearanceprews8.png[/IMG]


[IMG]http://img299.imageshack.us/img299/5924/screenshotgnomeappearanri0.png[/IMG]

I tried to solve this problem by installing **Fusion Icon, Emerald Theme Manager and GL Desktop.** But I am unable to solve this problem. When I try to launch Fusion Icon nothing happens though it is installed like the other two mentioned above.

My system specs are as follows:

[COLOR=SeaGreen]Intel C2D E4300 processor (1.8 GHz), 3 GB DDR2 667 MHz RAM with X3000 INTEL On Board Graphics. [/COLOR]

Could someone help me please? :confused: :(

Thank you.

---

### Post by runemaste644 on 2008-01-02
Are you sure you are not using the vesa driver?

---

### Post by src2206 on 2008-01-02
> **runemaste644 said:**
> Are you sure you are not using the vesa driver?

Please tell me how to check that..! :confused:

---

### Post by Ub1476 on 2008-01-02
[Blacklisted.]("http://ubuntuforums.org/showthread.php?t=582112")

Maybe the latest drivers from Intel works without issues.

You can test compiz by running this in the terminal:

```
SKIP_CHECKS=yes compiz
```

---

### Post by src2206 on 2008-01-02
Thanks for letting me know :(

But I'm **not** getting any error Message as below:

> Blacklisted PCIID '8086:2972' foundStill, I am presently checking whether there is any new driver update available or not. :!:


[COLOR=DarkRed][B]***EDIT***

[/B][COLOR=Black]It appears that my Display Driver is the latest version available (I checked through Device manager> Display Adapter> Intel(R) G965 Express Chipset Family. Though I am not 100% confident, as I do not usually meddle with drivers. My board is based on **Intel G965 Express** Chipset family. If you find otherwise, please be kind enough to post the download link here for the latest driver.[/COLOR]
[/COLOR]

---

### Post by src2206 on 2008-01-02
Ok, I have confirmed that I have the latest VGA driver installed.

So if I use the following command:
> SKIP_CHECKS=yes compiz

to test Compiz, can I revert back in case of emergency using

> SKIP_CHECKS=no compiz
?
Please let me know.

Thank you.

---

### Post by src2206 on 2008-01-03
Ok I tried the above command and it seems to be working without any problem, except the Terminal Window remains open, and closing that makes things go haywire.
But I could not customize Compiz. **Fusion Icon** still did not work. Could any one please tell me how to customize Compiz and its effects?

Thank you.

---

### Post by src2206 on 2008-01-03
There is a Graphics Driver available for Linux from Intel here: [http://downloadcenter.intel.com/Detail_Desc.aspx?agr=N&Inst=Yes&ProductID=2529&DwnldID=13815&strOSs=39&OSFullName=Linux*&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=N&Inst=Yes&ProductID=2529&DwnldID=13815&strOSs=39&OSFullName=Linux*&lang=eng)

Should I download this one?

Please suggest. :(

---

### Post by src2206 on 2008-01-05
Anyone please......?????!!!! :(

---

### Post by Ub1476 on 2008-01-05
For the SKIP_CHECK yes command to take effetc you need to follow the sticky on top of this forum (Have you been blacklisted?). I'm not sure if you should use the latest Intel driver or not. Probably some googling or makeing a new thread about that question would figure it out I guess.

If you want to stick with the provided driver, I suggest you try things like Video playback, performance etc, before you do any changes. If somethings get messed up thought, the "SKIP_CHECK yes" can be changed to "no" in /home/user/.config/compiz/compiz-manager.

---

### Post by src2206 on 2008-01-14
Ok



I can use Compiz, but I have no idea how really it happened. :huh: 

So here are the chain of events that took place:

I updated my Ubuntu installation completely including all the necessary and recommended updates.

Following Ubuntu community guide used Emerald theme manager to download all the GPL'd themes.

I reinstalled **Fusion Icon**. 

And as I clicked on the **Fusion Icon**, Voila!!! it is working! The Fusion Icon  displayed another small icon on the panel through which I just had to change the window manager **to Compiz from Default Metacity**.

Honestly, I have no idea why and how things fell in place.

Thanks very much for your help and I hope this post will help others with same issues as mine.

See the Screen shots 1 and 2 for Compiz in action. Its really great.

[[IMG]http://img205.imageshack.us/img205/8518/screenshotfq2.png[/IMG]]("http://imageshack.us")

[[IMG]http://img258.imageshack.us/img258/1043/screenshot1pv7.png[/IMG]]("http://imageshack.us")

I have tried Compiz on 7.04 with a nVidia card (and with constant help from Dougfractal) in another PC, but it never looks so much great. :D

---

