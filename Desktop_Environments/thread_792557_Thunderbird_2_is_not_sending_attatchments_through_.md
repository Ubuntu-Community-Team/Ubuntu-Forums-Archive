---
title: "Thunderbird 2 is not sending attatchments through gmail"
date: 2008-05-13
forum: Desktop Environments
---

### Post by andreseso on 2008-05-13
Hello,

I got Thunderbird configured to send email through my gmail account.  Everything was working until I upgraded to 8.04 but afterwards whenever I try to send an attachment, it freezes before sending it.  Just today I tried to send a 2MB jpg file and it froze at 14%

Is there any change in how I should configure Thunderbird to send emails through gmail?  I currently have configured smtp.gmail.com:587 using TLS and authentication.  Messages without attachments are sent without any problems

Thanks,
Andres

---

### Post by ajopaul on 2008-05-13
had used tb earlier with gmail, rite now using evolution, its pretty ok..

---

### Post by gnivler on 2008-05-13
Just trying to do something very similar, sending a large JPG through gmail using Thunderbird (version 2.0.0.14 (20080505)) and it seems I'm replicating the problem.  It stopped around 15%, after a minute I got an error dialog.  Trying it again it went to 50% and the error appears again:

Sending of message failed.
The message could not be sent because connecting to SMTP server smtp.gmail.com failed.  The server may be unavailable or is refusing SMTP connections.  Please verify that your SMTP server setting is correct and try again, or else contact your network administrator.

Tracerouting doesn't reveal any obvious network trouble.  Seems like the likely answer is the smtp server itself may be the cause but it's a guess.  Probably the easiest workaround, if you can do it, would be to use the smtp server of your ISP.  (*Update:  works fine with another smtp server*)

edit:  maybe something is up with my route, this trace looks a bit odd, getting extra replies:  

```
 6  74.125.48.249  96.246 ms  69.062 ms  78.034 ms
 7  66.249.94.90  78.031 ms 66.249.94.92  82.652 ms 66.249.94.90  82.522 ms
 8  72.14.232.66  81.355 ms 72.14.236.142  59.005 ms 72.14.236.138  57.356 ms
 9  72.14.205.109  49.211 ms  53.045 ms  53.100 ms
```

Not sure what it implies if anything.

---

### Post by andreseso on 2008-05-13
I had no problems with Thunderbird and gmail with Gutsy.  The issues only appeared when I upgraded to Hardy. I could send the emails using another smtp connection, but then my messages would not appear in the gmail web interface.  I'm not that fond of Evolution.

It'd be great to sort out the problems that appeared in Hardy with Thunderbird and gmail.

edit: My traceroute
```
10  72.14.232.94 (72.14.232.94)  75.276 ms 72.14.232.104 (72.14.232.104)  72.784 ms 72.14.233.105 (72.14.233.105)  72.359 ms
11  72.14.232.201 (72.14.232.201)  74.108 ms  75.769 ms 209.85.252.4 (209.85.252.4)  66.345 ms
12  72.14.232.167 (72.14.232.167)  67.746 ms  67.921 ms 72.14.232.190 (72.14.232.190)  69.701 ms
13  fg-in-f109.google.com (72.14.221.109)  61.784 ms 209.85.250.46 (209.85.250.46)  69.890 ms fg-in-f109.google.com (72.14.221.109)  63.094 ms

```

Thanks,
Andres

---

### Post by Thirtysixway on 2008-05-13
I thought you used port 465 for smtp.gmail.com but I can't be sure.  Try changing the port.

---

### Post by gnivler on 2008-05-13
> **andreseso said:**
> I had no problems with Thunderbird and gmail with Gutsy.  The issues only appeared when I upgraded to Hardy. I could send the emails using another smtp connection, but then my messages would not appear in the gmail web interface.  I'm not that fond of Evolution.

It'd be great to sort out the problems that appeared in Hardy with Thunderbird and gmail.

edit: My traceroute
```
10  72.14.232.94 (72.14.232.94)  75.276 ms 72.14.232.104 (72.14.232.104)  72.784 ms 72.14.233.105 (72.14.233.105)  72.359 ms
11  72.14.232.201 (72.14.232.201)  74.108 ms  75.769 ms 209.85.252.4 (209.85.252.4)  66.345 ms
12  72.14.232.167 (72.14.232.167)  67.746 ms  67.921 ms 72.14.232.190 (72.14.232.190)  69.701 ms
13  fg-in-f109.google.com (72.14.221.109)  61.784 ms 209.85.250.46 (209.85.250.46)  69.890 ms fg-in-f109.google.com (72.14.221.109)  63.094 ms

```

Thanks,
Andres

Tried smtp.gmail.com using SSL on 465 instead of TLS on 587, getting the same results.  I'm with you on Evolution, but it might be interesting if only as an experimental control, to see if it's the mail client or the network in some way.

---

### Post by andreseso on 2008-05-24
In effect, smtp.gmail.com through SSL at port 465 does not work either. Any ideas on how to send attachments through gmail using Thunderbird?

Thanks,
Andres

---

### Post by doubtful wisdom on 2008-08-19
I also cannot send attachments of any size.  Thunderbird nor Evolution allow me to send anything other than email and very small attachments.  This experience is with Gmail and NetZero POP email accounts.  This appears to be an Ubuntu problem, since Thunderbird under Windows works just fine on both NetZero and Gmail.

I so seldom use Windows that it took a while to realize that it was not a problem with Gmail or NetZero or my email programs.  Cannot find a bug report on this.  The two of you are the only other reports of this problem I have found.  

For now, I must use Windows for sending attachments.  I suspect that I have the same problem on my desktop at work as well, but have not verified it.  Did not have the problem with Gutsy.  Seldom send large files, so it took me a while to see this problem.

---

### Post by willix on 2008-09-09
I've got the same problem: Ubuntu Hardy, Thunderbird, Gmail and trouble sending large attachments.
I am able to send email with no attachments and successfully sent a small jpg (<1MB) but failed to send anything bigger. 

Same message as gnivler, usually when it reaches 98% of the sending.

I've got several smtp servers set in thunderbird and suspected that was the problem, but after fiddling arround with my properties, it did not look like that was the cause.

Anyone solved this?

---

### Post by willix on 2008-09-11
I'm not sure anybody is still reading this thread, nevertheless, since I'm still having problems sending attachments with Thunderbird and Gmail, I'm still trying to solve it, and I'll try keeping this thread updated.

I initially thought (and kinda hoped) Thunderbird (or a setting in it) was the cause. But I opened an account with a different provider than gmail and have successfully sent big attachments with Thunderbird to it. So that would seam to rule out Thunderbird. Or it might be a mix between the two...

Next step: test Gmail with evolution.

If somebody HAS solve this issue or know something about it, please let me know, thanks

---

### Post by willix on 2008-09-11
Evolution does slightly better than ThunderBird. Was Able to send a jpg that had previously failed with Thunderbird but then when sending a realy big file (5MB), it fails, or rather does not do anything... (0% complete)

Can someone point me to where evolution logs error messages so I can at least try and figure out what's going wrong?

---

### Post by meland on 2008-09-14
I seem to be having a similar problem.  New Ubuntu user (8.04 Desktop) running Thunderbird 2 through a university network to my Bluehost account.  I am not able to send messages with attachments larger than approximately 200 kB.

---

### Post by AlesUbu123 on 2008-10-06
Thanks God there are other people having the same problem (problematic are files larger than 200kB or more). This has been bugging me for months and I have posted several posts here but with no response!
This makes me have to open my browser and got gmail.com every time I send attachments through my gmail account!
Can anyone also look into this?
Could this be related to firewall, closed ports, etc??

Thanks for any help!

---

### Post by pagaNs on 2008-11-12
I have to report the same issue.
3 days ago, I have installed previous ubuntu distro and upgraded 2 times to get 8.04 LTS. Didn't installed anything before upgrades.
When in 8.04, I installed usual apps: aMSN, TB etc...
PROBLEM:
Sending .doc, that is 4 pages big with jpeg inserted in it (about 5MB+), as an attachment in Evoulution produces state where you see progress bar not moving with message "sending..." 0%.
I have installed TB then, and the problem is slightly different. Could send short msgs, but when sending THIS e-mail, operation brake with message:
Sending of message failed.The message could not be sent because connecting to SMTP server smtp.gmail.com failed.The server may be unavailable or is refusing SMTP connections.... on 15%|55% w/e
Tried changing from TLS port 587 - default port 25 
to
SSL port 587 - default port 465
and nothing changed.
On windouz, it worked fine...but I want to use Ubuntu as I used it before
PLZ HELP, I stopped playing wow, so I could use this system(I'm serious)
TNX IN ADVANCE
Davidov Ivan

---

### Post by yobser on 2008-12-09
I've got the same problem. But I noticed that from time to time I could not send message with any attachments and can send with attachments more then 2 MB.
I think reason in timeouts. But we can not handle smtp timeouts for thunderbird.

---

### Post by samden on 2008-12-09
Just checking you have it configured as per Google´s recommendations:
[http://mail.google.com/support/bin/answer.py?hl=en&answer=77662](http://mail.google.com/support/bin/answer.py?hl=en&answer=77662)

Obvious place to start, you have probably already done this yourself, if so another reader may find the link useful.

---

### Post by CyberAngel on 2008-12-10
I`ve got the same problem too...

If you try 10 times you might be lucky to send it once, but of course this is very annoying...

---

### Post by yobser on 2008-12-12
I noticed that some guys very happy with Evolution. And I installed it. More exactly I configured it for working with gmail. And I was surprised, that I also could not sent messages this attachments and message more than 1kb. I do not know what is the main reason and some one (may be Google) should answer why is it so.

---

### Post by andreseso on 2008-12-13
I just sent a 6MB attachment through Thunderbird using gmail.  It seems the problem has been solved in Intrepid Ibex.  I upgraded as soon as possible

As Hardy Heron is a LTS, it would be convenient to apply the necessary upstream changes to make sending email through gmail possible.  If not, there is always the upgrade path.

Thanks to all,
Andres

---

### Post by CyberAngel on 2008-12-13
> **andreseso said:**
> I just sent a 6MB attachment through Thunderbird using gmail.  It seems the problem has been solved in Intrepid Ibex.  I upgraded as soon as possible

As Hardy Heron is a LTS, it would be convenient to apply the necessary upstream changes to make sending email through gmail possible.  If not, there is always the upgrade path.

Thanks to all,
Andres

Try send many more 6MB attachments (or more) and tell us the results....
Sometimes it is also possible for me to send but sometimes not...
I don`t think that the problem has to do with the ubuntu version cause I always had/have it.

---

### Post by yobser on 2008-12-24
I did not have this problem until may and till I moved from Windows to Linux at all.

So, I think or Google did some changes or something wrong in network settings of mine. Because if I increase background utilization of my channel probability of getting error growths up.

Does anyone know how to adjust settings?

---

