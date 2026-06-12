---
title: "clock wont stay set"
date: 2009-01-23
forum: General Help
---

### Post by thingy87654321 on 2009-01-23
i am running ubuntu 8.10, the clock wont stay set, it set it like 43 times, same with my friends laptops


also will ubuntu run on a computer with a celeron 1 processor and 256 mb of ram? and will it run on a computer with a pentium 2 processor with 256 mb of ram?

---

### Post by cariboo on 2009-01-23
To rectify youor clock problem, check that you have it set for the right time zone, DOuble click on the clock and click on the Location dropdown and make sure it is set to your timezone, If that doesn't work, you may need to replace the CMOS battery on your motherboard. Take off the side panel (assuming you are using a desktop computer, you should see tha battery, it is about the size of a Canadian/US quarter.

The answers to questions 2 + 3 is yes, I would suggest using the [alternate iso]("http:///releases.ubuntu.com/8.10/") to install as the LiveCD needs 348MB  of ram to install.

Jim

---

### Post by thingy87654321 on 2009-01-23
it is set to fresno, thats where i live, i have a laptop, i have replaced the cmos battery to see if that was the problem a week ago,

---

### Post by afbase on 2009-01-23
you could make a cronjob that resynchronizes the clock every minute (if you feel thats  how often it would be necessary).

```

sudo crontab -e

```in the editor, try putting the following:
```

00-59 * * * * ntpdate ntp.ubuntu.com

```

---

### Post by mcduck on 2009-01-24
what version of Ubuntu you are running, and could you describe how the time changes (couple of minutes, or full hours, while computer is running or only when the machine is booted etc)

If you are running Ubuntu version 8.04 or older, they are still by default following the Unix tradition of assuming that your CMOS clock is running in UTC instead of local time.. (this is quite simple to change)

---

### Post by thingy87654321 on 2009-01-24
intrepid ibex (ubuntu 8.10) with all updates installed and it is about a 4 hour change

---

### Post by dcstar on 2009-01-25
> **thingy87654321 said:**
> intrepid ibex (ubuntu 8.10) with all updates installed and it is about a 4 hour change

```
sudo tzselect
```

---

### Post by Hobgoblin on 2009-01-25
About or exactly?

And does the system only run Ubuntu or does it also run Windows?

---

### Post by thingy87654321 on 2009-01-25
exactly a four hour change

---

### Post by thingy87654321 on 2009-01-25
and i only have ubuntu installed, why do you ask?

---

### Post by Hobgoblin on 2009-01-25
> **thingy87654321 said:**
> exactly a four hour change

Are you sure you have the timezone set correctly?

System > Administration > Time and Date

Is Configuration set to manual or keep synchronised with internet servers?

---

### Post by thingy87654321 on 2009-01-25
i fixed it by googleing it, takes less time to get a response

---

### Post by Doncr on 2009-02-08
> i fixed it by googleing it, takes less time to get a response 

Well thank you for sharing your solution with us.

---

### Post by 73ckn797 on 2009-02-08
And the solution was? Googling? That does not help very much.

---

### Post by thingy87654321 on 2009-02-09
i googled it and it gave me instrucyions on how to make it set by internet and another command to make it refresh the time every minute and now it works, i cant remember the command tho

---

### Post by Cuba71 on 2009-02-11
I have a somewhat related question.  I'm running 8.10 and every time I boot my laptop, the time zone defaults to Africa, and I have to manualy reset it every time..
It must be a config file that I could change to make it persistent.
Thank you.

---

### Post by thingy87654321 on 2009-02-11
make it its  own post because i really cant help =( sorry

---

### Post by abn91c on 2009-02-12
> **thingy87654321 said:**
> i am running ubuntu 8.10, the clock wont stay set, it set it like 43 times, same with my friends laptops


also will ubuntu run on a computer with a celeron 1 processor and 256 mb of ram? and will it run on a computer with a pentium 2 processor with 256 mb of ram?
If your old pc uses Pc100/133 RAM you can buy more here [http://www.geeks.com](http://www.geeks.com)

---

### Post by thingy87654321 on 2010-08-01
sorry for resurrecting a old thread i made BUT, im not on 9.1o, the clock is wrong, but if i click the clock and then click locations, it says fresno and it has the correct time listed there, but not on the toolbar.... is this a bug or just something up with my computer, this is the same computer from last time i think, well with a new motherboard, last one cooked itself in my laptop bag untill the southbridge traveled and shorted out, frying the board, got a new motherboard, lose connection on the nortbride, baked it in the oven, all is well now

---

### Post by thingy87654321 on 2010-08-01
nevermind, sorry, it was a bios issue this time, well not bios really, there was a broken pin on the cmos battery connector, the battery doesnt go directly on the board, it connects through a 2 pin connector, the negative pin broke off from the board, so i just connected the negative wire to the chassis ground (aka screw hole ground) and all is well

---

### Post by thingy87654321 on 2010-08-01
> **abn91c said:**
> If your old pc uses Pc100/133 RAM you can buy more here [http://www.geeks.com](http://www.geeks.com)

Thanks but that computer has been replaced with a much better one, i didnt wanna pay monney to get ram for a older machine,

---

