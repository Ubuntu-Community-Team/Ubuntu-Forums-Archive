---
title: "computer is really slow.  should i downgrade from Hardy?"
date: 2009-01-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by chee on 2009-01-09
i have been using Ubuntu for about 3 years now and it has worked great so far.  my computer has been really lagging lately and i don't know why.  i am just wondering if there is any advantage to going back to an older version of Ubuntu.  i wouldn't think so but i don't know much really.

my computer is a Dell Insiron 6400.  the hard drive is not full as i have about 40 GB freespace of 120 (10 of which is for windows).  the only other thing i would think of was that maybe the cooling system needs to be cleaned,  all the little tubing duct work.  i have gkrealm to monitor the temp and it seems to run hot pretty easily.

recently i have been trying to burn DVDs which worked fine and it lagged so much that the DVDs won't work properly.  i have changed nothing but updates.

again,  i realize that the newer version of Ubuntu probably isn't my problem but do i really need it?  all i do surf the net and burn DVDs occasionally.

any help would be great.  thank you very much.

---

### Post by AlanR8 on 2009-01-09
Sorry to hear of your issues. I assume that because you've been running Ubuntu for quite a while now you've run the "top" command in a terminal to find out what processes are running? 

Or, if you don't like the command line, pressing Ctrl + Esc will bring up a graphical representation of all the processes running. Now you can see what's going on and if you find a process that's hogging all your processor power, find out what it does or is related to and IF SAFE kill it!

---

### Post by chee on 2009-01-09
i have gone into the Systems then admin menu and went to system i think and found the processes there.  same  thing?

---

### Post by AlanR8 on 2009-01-09
Sounds about right....I use Kubuntu not Ubuntu, but when I press Ctrl + Esc this is what pops up.

See attached image and note the VERY low processor utilisation!

---

### Post by chee on 2009-01-09
so my next question is how do i find out which processes i need and which i don't?

---

### Post by AlanR8 on 2009-01-09
chee. 

Look at the list in your "task manager" for want of a better description, and see what process is hogging the processors time, if any. 

As you saw on my list the CPU usage was very low. You can sort the columns in any order you want so I normally sort my CPU use, highest first.

If it's a known program like Firefox just select it and kill it then see how the computer responds. I had a similar issue the other day to you and in my process list I saw MPlayer was running at about 80% CPU usage. Odd because I hadn't run MPlayer! Then I realised I use the MPlayer plug-in in Firefox and it had gone rogue. I just killed the process and all was well again.

Good luck. I'm NOT an expert in what needs to run and what doesn't so maybe one of the gurus can help out here as well.

---

### Post by chee on 2009-01-09
thanks,  that is exactly the description i was looking for.  i use the task manager on my work computer that runs windows but i wasn't sure about ubuntu and my computer is at home.  i will check it out tonight.  thanks again

---

### Post by linux_tech on 2009-01-09
> **chee said:**
>  the only other thing i would think of was that maybe the cooling system needs to be cleaned,  all the little tubing duct work.  i have gkrealm to monitor the temp and it seems to run hot pretty easily.

Cleaning the dust out is a good idea, on laptops, just lift off the keyboard and then with a can of air, spray the dust out away from it. You should be able to see the air vents on the back of the case, w/ some copper cooling fins. The dust usually gets stuck in the cooling fins. 
If its 3 years old, chances are there is some dust build up.  Its a good idea to clean them once a year.

Using cooling mats also help keep the laptop cooler-
[http://www.targus.com/us/accessories_cooling.asp](http://www.targus.com/us/accessories_cooling.asp)

You can also regulate the fan speed (speed it up), but best to spray clean first

---

