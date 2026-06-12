---
title: "[Script question] how to pass script parameters"
date: 2006-08-18
forum: Desktop Environments
---

### Post by latebeat on 2006-08-18
Hello,

I'm experimenting with scripts and I have one simple question!
How do you pass script parameters in the command line? :)

For example I want to create a script that records streaming radio stations.

It's all still on my mind so I'll post in pseudo code:

```

#DEFINE URLS:
Station1URL=http://blabla
Station2URL=http://blablah
Station3URL=http://blablah

mplayer record **station**
sleep **time**  #time is the recording time
killall mplayer

```

so how can I pass the bold parameters through the command line? Say:
```
sh .radiorecord Station2URL 2h
```

Also can you tell me any forums that are more appropriate for scripting questions?

thanks!

---

### Post by ohgod on 2006-08-18
Check out paragraph number 6 on this page:
[http://floppix.ccai.com/scripts1.html]("http://floppix.ccai.com/scripts1.html")

---

### Post by anthro398 on 2006-08-18
I use the [ABS]("http://www.tldp.org/LDP/abs/html/").

---

### Post by latebeat on 2006-08-18
> **ohgod said:**
> Check out paragraph number 6 on this page:
[http://floppix.ccai.com/scripts1.html]("http://floppix.ccai.com/scripts1.html")

Thanks that was a very useful example however if I pass $1 as a parameter it is not treated as a variable.
For example

radiorecord Station1URL is passed as "Station1URL" to mplayer and is not substituted as "http://blabla" (since it is also a variable). 

Any ideas?

---

### Post by bensexson on 2006-08-18
mplayer record http://$1 http://$2 http://$3
sleep time  #time is the recording time
killall mplayer

---

### Post by latebeat on 2006-08-19
> **bensexson said:**
> mplayer record http://$1 http://$2 http://$3
sleep time  #time is the recording time
killall mplayer

mm that doesn't help a lot. You see in the script I have 10 variables with the different radio station urls which saves me from the trouble of finding the individual url each time. What I want is to pass one of them as parameters in the command line..

so sh record.sh station1 2h would read the script, pass the station1 url to the mplayer command and then sleep for 2h which is the recording time.
However with just $1, $2 it doesn't work because positional parameter 1 ($1) isn't checked against the existing variables in the script in order to interpret the station1 name as its url.

---

### Post by bensexson on 2006-08-19
OK, do you have 10 variables in the script that each contain a URL of a stream?  If so you may want to take a look at using the case command and passing $1 to the case command and have 10 cases in the script.  One for each  stream and the default for a bad input for $1.

---

