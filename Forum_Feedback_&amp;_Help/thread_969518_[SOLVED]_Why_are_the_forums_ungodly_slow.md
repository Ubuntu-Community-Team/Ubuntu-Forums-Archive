---
title: "[SOLVED] Why are the forums ungodly slow?"
date: 2008-11-03
forum: Forum Feedback &amp; Help
---

### Post by bwhite82 on 2008-11-03
I've noticed this the last few months. Just navigating the forums is very slow for me. I don't think its my connection, other websites are fine/run fast. For instance clicking on the logo to browse the main index -- it can take up to 20 seconds sometimes to display this! Other times its near instantaneous. Is it a database issue? I've pinged the server to check, it gets fast response times there so that's why I think maybe database. Also creating or responding to posts is time consuming as well.

I dunno, its getting quite annoying. Is there any settings I can do on my end to help? Firefox or something? Is the server load too much for the amount of users here?


-Browsing slow in Ohio, USA

---

### Post by Joeb454 on 2008-11-03
The forums have been like this for a while - hopefully we should be getting better hardware soon. It's on the agenda for the forum council meeting :)

---

### Post by schauerlich on 2008-11-03
> **Joeb454 said:**
> The forums have been like this for a while - hopefully we should be getting better hardware soon. It's on the agenda for the forum council meeting :)

FC meeting agenda:
1) Talk about how cool it is to be admins
2) Make fun of Joeb454's accent
3) Beg (and be rejected by SABDFL) for moar hardware
4) GOTO 1)

---

### Post by bwhite82 on 2008-11-03
I think the community would be willing to donate hardware (I know I would be) as long as were not talking about an entire new server for instance.

---

### Post by lisati on 2008-11-03
> **EDavidBurg said:**
> FC meeting agenda:
1) Talk about how cool it is to be admins
2) Make fun of Joeb454's accent
3) Beg (and be rejected by SABDFL) for moar hardware
4) GOTO 1)

Rewriting this in a manner that will please those who don't like "GOTO" is left as an exercise for the reader.

---

### Post by lifestream on 2008-11-03
Mmm... You could try disabling images in Ubuntu forums :) Might make it a little faster.

---

### Post by Joeb454 on 2008-11-03
> **EDavidBurg said:**
> FC meeting agenda:
1) Talk about how cool it is to be admins
2) Make fun of Joeb454's accent
3) Beg (and be rejected by SABDFL) for moar hardware
4) GOTO 1)

Use of a GOTO statement now results in an instant ban, didn't you get the memo?

---

### Post by DrMega on 2008-11-03
> **lisati said:**
> Rewriting this in a manner that will please those who don't like "GOTO" is left as an exercise for the reader.

```

while(1==1)
{
  1) Talk about how cool it is to be admins
  2) Make fun of Joeb454's accent
  3) Beg (and be rejected by SABDFL) for moar hardware
}

```

---

### Post by Joeb454 on 2008-11-03
> **Soldierboy said:**
> I think the community would be willing to donate hardware (I know I would be) as long as were not talking about an entire new server for instance.

It would require a whole new server (hopefully more than 1)

---

### Post by lukjad on 2008-11-03
Joeb454 had an accent?

---

### Post by imbjr on 2008-11-03
> **DrMega said:**
> ```

while(1==1)

```

Oh, dear, a GOTO is nasty, but what you got there is a no-no too.

---

### Post by estyles on 2008-11-03
> **imbjr said:**
> Oh, dear, a GOTO is nasty, but what you got there is a no-no too.

How about: ```
while(strlen("LOOPFOREVER")==strlen("LOOPFOREVER"))
```

---

### Post by Joeb454 on 2008-11-03
[php]while(!true)
{
   ...code...
}[/php] :p

---

### Post by bwhite82 on 2008-11-03
Wow, thread officially hijacked.

---

### Post by Joeb454 on 2008-11-03
Good point - back on topic. I blame Edavidburg.

As I mentioned - the forum hardware isn't the best hardware - forums this size shouldn't be run on the current hardware we have. And hopefully we will be getting more soon :)

---

### Post by Joeb454 on 2008-11-03
Good point - back on topic. I blame Edavidburg.

As I mentioned - the forum hardware isn't the best hardware - forums this size shouldn't be run on the current hardware we have. And hopefully we will be getting more soon :)

---

### Post by billgoldberg on 2008-11-03
The forum is frustratingly slow.

Loading page takes at least 10 seconds, trying to reply takes at least 20.

It's becoming unusable.

---

### Post by DrMega on 2008-11-03
> **imbjr said:**
> Oh, dear, a GOTO is nasty, but what you got there is a no-no too.

Yep, you're right, it's nasty.

Actually a GOTO has, as far as I'm aware, a grand total of ONE use in C. Imagine you have some conditional loop that has many nesting levels, and some condition in the inner most loop can kill the need for the whole loop so you want to resume after the end of the outermost loop, then a GOTO to break you out (wrapped inside an 'if' block) saves having to test the criteria on every loop level on the way out. It's a technique I've never used but I can see the point if you are working on extremely limited hardware such as a really old embedded controller or something.

---

### Post by sisco311 on 2008-11-03
> **Joeb454 said:**
> [php]while(!true)
{
   ...code...
}[/php] :p

or

```
#define EVER (;;)

int main()
{
  for EVER
  {
    ...
    cout<<"Make fun of Joeb45..."<<endl;
    ...
  }
}

```;)

---

### Post by lukjad on 2008-11-03
I have ***got*** to learn to code.

---

### Post by pp. on 2008-11-03
> **sisco311 said:**
> or

[CODE]#define EVER (;;)

!true!=true:confused:

---

### Post by Yellow Pasque on 2008-11-03
> Why are the forums ungodly slow? I've noticed this the last few months.
- The Ubuntu Hardy LTS release enticed a lot of people to try Linux for the first time and subsequently created a lot of forum traffic.
- FF/Mozilla is slow (3.1 should speed rendering up). Anyway, if you have Ubuntu Intrepid, try browsing the forums with Epiphany (with Webkit backend) to see how much lag is due to the browser vs. the network:
```
sudo apt-get install epiphany-webkit
```

---

### Post by MasterNetra on 2008-11-03
I know when i had hardy 64bit firefox was pretty fast for me even on the forums but now that i've switch to Interpid 32bit it slows up at times. But thats probably because i downgraded to 32bit. :p Wanted to install adobe air so i can install finetune desktop player. Naturally it all installs but finetune don't run x.x then again its ment for windows and adobe air didn't try to tap wine to install finetune so theres the problem right there :p ...

---

### Post by bwhite82 on 2008-11-03
> **Temüjin said:**
> - The Ubuntu Hardy LTS release enticed a lot of people to try Linux for the first time and subsequently created a lot of forum traffic.
- FF/Mozilla is slow (3.1 should speed rendering up). Anyway, if you have Ubuntu Intrepid, try browsing the forums with Epiphany (with Webkit backend) to see how much lag is due to the browser vs. the network:
```
sudo apt-get install epiphany-webkit
```

Wow! The rendering is VERY fast with epiphany, however, I still have to wait for the server first unfortunately. So its like:

wait for it...wait for it...wait for it...wait for it...BAM!

---

### Post by coffeecat on 2008-11-03
> **lukjad007 said:**
> Joeb454 had an accent?

Don't we all? :?

---

### Post by LaRoza on 2008-11-03
> **lukjad007 said:**
> Joeb454 had an accent?

He comes from a place with a name straight out of Hot Fuzz. Of course he has an accent. Now the question is, which one?

---

### Post by lukjad on 2008-11-03
> **LaRoza said:**
> He comes from a place with a name straight out of Hot Fuzz. Of course he has an accent. Now the question is, which one?
I heard no accent.

---

### Post by Elfy on 2008-11-03
I did loike

---

### Post by Joeb454 on 2008-11-03
Keep guessing :D

---

### Post by lukjad on 2008-11-03
I still hear no accent.

---

### Post by schauerlich on 2008-11-03
> **lisati said:**
> Rewriting this in a manner that will please those who don't like "GOTO" is left as an exercise for the reader.

[php]#!/usr/bin/env python

MeetingOver = False

while MeetingOver == False:
    mouth.speak("Isn't it really awesome how we're admins?")
    sarcasm.mock(Joeb454.accent)
    if NewHardware not in ServerRoom :
        mail.send("Oh master, could you spare us some silicon?", mark@ubuntu.com)
    else :
        MeetingOver = True[/php]

---

### Post by snova on 2008-11-03
Better, but [email]mark@ubuntu.com[/email] isn't legal Python syntax.

And anyway, we'll have new hardware quite soon now. From #ubuntuforums:

```
<jdong>	It's a DL385G5, with 8Gb of memory, 2 Quad Core 2.3Ghz Opterons and
<jdong>	130Gb of local RAID 10 storage.  It'll go up to 16Gb in a week or so
<jdong>	and more disk too,
```

I thought Joeb454 was British? Or am I missing the point of it all (as usual)?

---

### Post by Joeb454 on 2008-11-03
I am British :)

---

### Post by LaRoza on 2008-11-03
> **Joeb454 said:**
> I am British :)

Sorry to hear that. I hope you get better.

---

### Post by Joeb454 on 2008-11-03
> **LaRoza said:**
> Sorry to hear that. I hope you get better.

The doctors say it will be a long and painful process, but it can be cured

---

### Post by Elfy on 2008-11-04
I was hoping that the cure would take less time than it has to date, there is still no sign of any change here - I think I was given a placebo.

---

### Post by lukjad on 2008-11-04
Well, now that you know that, you just got rid of any possible use it had.

---

### Post by bwhite82 on 2008-11-08
Thank you! HUGE improvement here.

---

