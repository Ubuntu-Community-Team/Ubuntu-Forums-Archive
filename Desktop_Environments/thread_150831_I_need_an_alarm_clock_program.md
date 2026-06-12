---
title: "I need an alarm clock program"
date: 2006-03-26
forum: Desktop Environments
---

### Post by mrpixels0 on 2006-03-26
I was wondering if anyone has written or knows of an application that i can program to start Rythem Box at a specific day, date and time ?. I want to use it as an alarm clock so i can get up at 5:00 am, my work schedule has permantly changed and i need a way to wake up on time.

I figure my computer never shuts down so why not use it :)  as an alarm clock.

thanks in advance for any and all help, with this strange request.

---

### Post by 5-HT on 2006-03-26
Hey, you could set up a cronjob ('cron' is a task scheduler) for it.
With a cronjob you can get Rhythmbox to start at the days/times you want.

Most likely, for the command given to cron to execute, you'd need to pass something for Rhythmbox to play at startup so you get something to wake you up with (i. e. /usr/bin/rhythmbox <path to song>).
I don't use Rhythmbox myself, but there should be an option to allow loading of a playlist you could use instead of the song. That may be covered in the Rhythmbox manual (man rhythmbox) or help documents.

It's really easy to set up a cron job, so I haven't gone into it here but I will reference some great manuals/guides.

For the wiki cron tutorial (quick and easy, describes all you really need at the superficial level): [https://wiki.ubuntu.com/CronHowto]("https://wiki.ubuntu.com/CronHowto")
For the cron manual: man cron
For the crontab manual: man 5 crontab

If you have any problems, just post back and someone here will be able to help you out.

As an obvious aside, it would be a good idea to test out the cron job prior to some important meeting/shift you need to wake up for!

P.S. If you wanted to go another route and just install an alarm clock, searching synaptic for 'alarm' yeilds quite a few options.

Hope that helps.

---

### Post by Patrick-Ruff on 2006-03-26
heh thats awesome, I'll have to try that. problem for me is, I FINALLY got used to waking up at a certain time and the time is going to go up an hour pretty soon.

---

### Post by mrpixels0 on 2006-03-26
thanks for great links 5-HT :), i am not a new user but i am not a pro user either i have been using Ubuntu since it first came out and mostly just used "as is" out of the box, so thanks for helping me out here (I always thought Cron some thing that was only for Mail systems and stuff) i only wanted music to wake up to becuase simple buzz's and beeps wont work, i would sleep right on through it :), but Ramstein at full volume on a six speaker home theatre is a little harder to ignore for long :D.

so far the guide links you posted are very easy to understand and i am learning somthing new at the same time for the first time, i feel kinda like i am getting somewhere with linux i had been putting it off for a long time feeling overwhelmed by the sheer number of command line programs and the parameters for each one. but i comming to realize i only have to learn the ones i need and can pretty much not worry about the rest.

thanks again guys for being there for a new guy.

MP0

---

