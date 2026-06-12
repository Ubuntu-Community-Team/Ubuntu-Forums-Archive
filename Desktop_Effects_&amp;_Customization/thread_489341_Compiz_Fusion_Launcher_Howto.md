---
title: "Compiz Fusion Launcher Howto"
date: 2007-07-01
forum: Desktop Effects &amp; Customization
---

### Post by OffHand on 2007-07-01
Hey guys,

For anyone who would to change between compiz and metacity, here is a way you can easily toggle between the two.

Open a blank text file and insert the code below:

```

#!/bin/sh

# click to start, click to stop

if pidof compiz.real
then
 exec metacity --replace
else
 exec compiz --replace -c emerald

fi

```

Save the file with a convenient name and make it executable. (Right click > Properties > Permissions > check: allow executing this file as a program)

Now you can double-click this file and choose run or make a launcher on your panel pointing to this file.

Note: If you are not using Emerald just use 'compiz --replace'.

I hope this is useful to someone.

---

### Post by steveneddy on 2007-07-01
Cool - this works well - thank you.

---

### Post by steveneddy on 2007-07-01
This should be a sticky. So many people could use this instead of running it (Compiz-Fusion) at start-up.

---

### Post by revertex on 2007-07-01
thanks, nice1

---

### Post by sabrewolf2006 on 2007-07-01
You could just leave beryl-manager running and set your wm to compiz (if you don't have the compiz from the repos installed too it should be the fusion version)

Then if it keels over for whatever reason you've got the manager to get you a working wm back :D

---

### Post by exploder on 2007-07-01
The script works perfectly! How can I get it to work as a launcher from the panel? I tried creating the launcher pointing to the script but I keep getting a "can't start child process" error.

Can anyone tell me what I am doing wrong?

---

### Post by autocrosser on 2007-07-01
1. Save the script to your user's home. (I called it compiz_start)
2. open a terminal &  chmod 777 '/home/"your_name"/compiz_start' 
3. Right click on a panel & select a "custom launcher"
4. call it whatever you want & in the command area put: /home/"your_name"/compiz_start
5. test it out:D

I used my Beryl Icon :)

---

### Post by exploder on 2007-07-01
Thanks autocrosser! That fixed things up real nice!

---

### Post by autocrosser on 2007-07-01
You're welcome---That's what the forums are for:guitar:

---

### Post by PRGUY85 on 2007-07-01
Yet is there any way to make it automatic on startup?  I have tried different methods to no success...

---

### Post by Bd0g on 2007-07-01
Thx for this shortcut :) 

Maybe something that should be included as a real launcher in the next version :)

---

### Post by autocrosser on 2007-07-01
You could put the "compiz --replace -c emerald --replace" in your Startup Programs tab in Sessions. I tried it but the first time Compiz ****ed out, I changed to this startup method.
It's better to be able to decide when you want it on/off---remember, it's still very beta;)

---

### Post by vexorian on 2007-07-01
thank you, now I can easily toggle between "show off mode" and "work mode"

---

### Post by revertex on 2007-07-01
launch compiz after metacity load, sleep is your friend

```
#!/bin/bash
sleep 10s && compiz --replace
```

---

### Post by OffHand on 2007-07-02
Glad you guys find it useful!  :D

---

### Post by autocrosser on 2007-07-02
Thanks--that is a great script!!

---

### Post by mikec13 on 2007-07-02
What's the point of putting "| grep [0-9]" in the script?

---

### Post by OffHand on 2007-07-02
> **mikec13 said:**
> What's the point of putting "| grep [0-9]" in the script?

grep [0-9] = {search for pairs of numeric digits}

Essentially it will check if compiz.real has a PID (which means it is running). The grep [0-9] command will look for any random number (To match a selection of characters you use []. [0-9] is the same as [0123456789] ). If it finds a number, it will execute  exec metacity --replace

---

### Post by mikec13 on 2007-07-02
> **OffHand said:**
> grep [0-9] = {search for pairs of numeric digits}

Essentially it will check if compiz.real has a PID (which means it is running). The grep [0-9] command will look for any random number (To match a selection of characters you use []. [0-9] is the same as [0123456789] ). If it finds a number, it will execute  exec metacity --replace
Won't it work the same if you take out the grep?  If the compiz.real process exists, pidof compiz.real will return a non-zero number, so the if statement will pass as true.  

If the process doesn't exist, 'if pidof compiz.real' should return as false.

---

### Post by walkerk on 2007-07-02
better icon to use instead of the beryl icon..

---

### Post by OffHand on 2007-07-02
> **mikec13 said:**
> Won't it work the same if you take out the grep?  If the compiz.real process exists, pidof compiz.real will return a non-zero number, so the if statement will pass as true.  

If the process doesn't exist, 'if pidof compiz.real' should return as false.

Actually... you are right. This will work also.

```

#!/bin/sh

# click to start, click to stop

if pidof compiz.real
then
 exec metacity --replace
else
 exec compiz --replace -c emerald

fi

```

---

### Post by autocrosser on 2007-07-02
I know--I just liked the Beryl one better----
 
 
> **walkerk said:**
> better icon to use instead of the beryl icon..

---

### Post by steveneddy on 2007-07-02
> **walkerk said:**
> better icon to use instead of the beryl icon..

Thanks for the icon.

---

### Post by Mega_Fauna on 2007-07-25
Thanks, this is beautiful and exactly what I needed:)

Came up w/ Google and NOT the Ubuntu forum search box. This should be easier to find if not packaged with the sofware (IMHO).

/Thanks again.

---

### Post by luckyd on 2007-07-25
look at my post  on this thread [http://ubuntuforums.org/showthread.php?p=3021908](http://ubuntuforums.org/showthread.php?p=3021908)

---

### Post by psyopper on 2007-07-25
Awesome!

Thank you very much!! Now all I need to do is track down that cool CompizFusion cube icon I saw around the forum...

---

### Post by steveneddy on 2007-07-25
> **psyopper said:**
> Awesome!

Thank you very much!! Now all I need to do is track down that cool CompizFusion cube icon I saw around the forum...

Uh - it's on page two of this thread.

Yet - here it is again.

---

### Post by psyopper on 2007-07-25
> **steveneddy said:**
> Uh - it's on page two of this thread.

Yet - here it is again.

Different ones, [I was looking for these]("http://ubuntuforums.org/showthread.php?p=3081546#post3081546"). Didn't find them as icons so I whipped them up myself, and in good FLOSS tradition shared them with everyone else.

:)

---

### Post by Floydius on 2007-08-22
First off, props to you, OffHand for figuring this out!  Just a note for all those who might be using beryl and kwin (for kde), this script worked perfectly for me as well (just replacing the program names):

```

 
#!/bin/sh

# click to start, click to stop

if pidof beryl
then
 exec kwin --replace
else
 exec beryl --replace

fi

```

Thanks, OffHand!

---

### Post by steveneddy on 2007-08-22
I changed the script a little for the conpiz-fission thing.

```


#!/bin/sh

# click to start, click to stop

if pidof compiz.real | grep [0-9] > /dev/null
then
 exec metacity --replace
else
 ** exec compiz --indirect-rendering --replace -c emerald**
fi


```

The indirect rendering makes it a little faster and it, I don't know, sparkles a little, or something.

---

### Post by exchequer598 on 2007-10-22
> **autocrosser said:**
> 1. Save the script to your user's home. (I called it compiz_start)
2. open a terminal &  chmod 777 '/home/"your_name"/compiz_start' 
3. Right click on a panel & select a "custom launcher"
4. call it whatever you want & in the command area put: /home/"your_name"/compiz_start
5. test it out:D

I used my Beryl Icon :)

Oh my god this helped me a lot!! Thank you so much..

---

### Post by autocrosser on 2007-10-22
Glad it worked for you!!!

---

