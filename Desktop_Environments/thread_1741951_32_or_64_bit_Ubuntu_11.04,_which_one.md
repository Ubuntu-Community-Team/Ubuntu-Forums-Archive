---
title: "32 or 64 bit Ubuntu 11.04, which one?"
date: 2011-04-28
forum: Desktop Environments
---

### Post by cybrsaylr on 2011-04-28
Should I select 32 or 64 bit version of 11.04?

 I've been using 64 bit Karmic and Maverick but I see Ubuntu recommends the 32 bit version of 11.04. How come they recommend 32 and not 64 bit? Which one is best?

---

### Post by 3Miro on 2011-04-28
> **cybrsaylr said:**
> Should I select 32 or 64 bit version of 11.04?

 I've been using 64 bit Karmic and Maverick but I see Ubuntu recommends the 32 bit version of 11.04. How come they recommend 32 and not 64 bit? Which one is best?

Some proprietary drivers have 32-bit versions only and historically 64-bit flash has been a bit iffy (although lately it has been working just fine). My rule is, if you have at least 2GB of RAM and you don't run into any issues with drivers and flash, then use 64-bit. Otherwise, go for 32-bit.

---

### Post by cybrsaylr on 2011-04-28
I've been running 64 bit Karmic since Nov 2009 with no problems. Same with 64 bit Maverick which I've been running since its later release. I have plenty of RAM. 

I'm also running 32 bit Maverick on an older P4 that can't handle 64 bit. 64 bit versions seem to run better for me but then again they are installed on newer PCs. 

Thanks for the input 3Miro.

Other input is also welcome.

---

### Post by THE CARTER on 2011-04-28
If you've been running 64-bit in the past, your computer should be able to run 64-bit.  How much RAM do you have?

---

### Post by yeti2011 on 2011-04-28
Your question is my same question.

I've been using 10.10 Ubuntu 64bit version on Acer Aspire 8930G Intel Core Duo with 4 GB ram and I only experienced some problems when linking LibreOffice Base 3.3.2 to postgresql 8.4 database via odbc drivers.

You may also refer to the article as in the following link: [http://www.muktware.com/man/1047](http://www.muktware.com/man/1047)[]("http://www.muktware.com/man/1047").

Anyway I think the best solution is to try both 32 and 64 bit version if you have multi-boot capabilities to check the best compromise between performance and compatibility for YOUR specific hardware equipment and related software requirements.

---

### Post by THE CARTER on 2011-04-28
As in, exactly.

---

### Post by THE CARTER on 2011-04-28
It sounds like you have enough ram (anything above 2GB can run 64 bit, however, running 32 bit will only let you use 2GB of memory).  then you should definitely run 64-bit to fully take advantage of your memory.

Most apps are compatible with 64-bit, so you should be good to go.

---

### Post by 3Miro on 2011-04-28
> **THE CARTER said:**
> It sounds like you have enough ram (anything above 2GB can run 64 bit, however, running 32 bit will only let you use 2GB of memory).  then you should definitely run 64-bit to fully take advantage of your memory.

Most apps are compatible with 64-bit, so you should be good to go.

32-bit normally runs 4GB total video + regular RAM. If you have a 1GB video card, you can use 3GB of RAM. If you have 256MB video card, you can use 3.7GB of RAM.

32-bit has the PAE kernel, which will let you use more than 4GB of RAM on a 32-bit machine. However, this is a hack and if you have that much RAM, you should use PAE only if you have some specific rare problem with 64-bit (i.e. on 4GB of RAM, 64-bit should be considered by default).

---

### Post by TBABill on 2011-04-28
I even run 64 bit Debian on a 1GB RAM older Athlon 64 x2 machine. It runs great and with your machine it is already proven itself well capable and possibly snappier on 64 bit. I wouldn't change unless you find a limitation where 32 bit serves you better.

---

### Post by cybrsaylr on 2011-04-28
> **THE CARTER said:**
> If you've been running 64-bit in the past, your computer should be able to run 64-bit.  How much RAM do you have?

I have plenty of RAM as listed in my sig. 
8GB DDR3 in desktop with a 1GB video card and 4GB in my laptop.

---

### Post by coffeenas on 2011-04-29
I too would like to know, specifically for 11.04.

There are a lot of misconceptions flying around the internets. The advantage of 64-bit is that it "generally" runs and loads faster and is backward-compatible with 32-bit programs, not vice-versa. The disadvantage is that it typically eats up a little more RAM to accomplish this. But there is no requirement that you use at least 4GB of RAM for either. If you were commonly maxing out 1GB RAM under 32-bit, 64-bit will be slower. But if you had plenty of un-utilized RAM in 32-bit, then 64-bit will be faster, even with only 1GB on RAM.

What I would like to know is why 32-bit 11.04 is recommended and can I ever install the 64-bit? I can only assume its because the code is glitchy as hell. I couldn't even install the 64-bit version, but 32-bit works fine.

---

### Post by cybrsaylr on 2011-04-29
I run both the 32 and 64 bit versions and have noticed 64 runs more efficiently and a tad faster. Haven't really had any problems with 64 bit going back to Karmic. I was just surprised to see 32 bit Natty recommended over 64 bit.

I downloaded and burned both 64 and 32 bit Natty. So far I installed 32 bit Natty in an older single core Dell 2.8Ghz P4 desktop that can't hande 64 bit. It was a smooth flawless install. It took an hour which surprised me and looks just like Maverick! Didn't get the 'new' Natty look. Don't know why. 

So far 32 bit Natty is running fine. All that was needed was to install Flash (Ubuntu Software Center easily did this) and mp3 plugins and it seems good to go. 32 bit Natty retained most of my settings and folders/files from prior Maverick. 

When I tested out the Natty 64 bit version it says it will wipe out everything from the previous Maverick partition it detected. Also it had the Maverick look and not the 'new' Natty look when I ran 64 bit Natty off the Install CD I had just created. The setups and installs are different between 32 and 64 bit Natty.

---

### Post by cybrsaylr on 2011-04-30
FWIW Installed 64 bit Natty on my laptop. 
Install was very smooth and took ~30 minutes. Install included Flash and mp3 plugins after checking then off in the install menu. Printer was installed also by simple plugging it in and turning it on during initial install. 

After that Natty was good to go. The 64 bit version runs fine so far and seemed to go faster and easier than the 32 bit version of Natty. It was a clean install and all settings from previous Maverick were lost. Luckily I knew this would happen and had backed up most of what needed saving by simply dumping it over into the Windows side of my dual boot setup.

Now I just have to get familiar with this new Unity look.

---

### Post by quasi13 on 2011-05-02
> **cybrsaylr said:**
> ... I was just surprised to see 32 bit Natty recommended over 64 bit.

Can anyone tell me why?  Elsewhere on the Ubuntu site, 64-bit is recommended if your system supports it.  It would make sense as a recommendation if most peoples' systems would only support 32-bit, but that doesn't explain why 11.04 would have this recommendation and 10.10 would not.

---

