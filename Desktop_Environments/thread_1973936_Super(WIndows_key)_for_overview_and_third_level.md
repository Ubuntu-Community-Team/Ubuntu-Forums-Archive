---
title: "Super(WIndows key) for overview and third level"
date: 2012-05-05
forum: Desktop Environments
---

### Post by TxP on 2012-05-05
Hello together,

I've got a little issue with ubuntu 12.04 which bugs me very much.
I'm using ubuntu with gnome 3 as the Desktop environment, where the windows key is used to get into the overview mode (same as in unity).
So far so good, I want to keep this behavior...
But I want the windows key also to be the third level chooser (at least for {}[] ).
The problem here is that I am working on a german keyboard on which you have to type those brackets with alt Gr + 7 ( or 8 9 0 respectively). This isn't very nice especially since I do a lot of programming where I need them all the time.
So if I change the third level chooser on win key the overview mode doesn't work anymore. The windows key must not become the third level chooser for all the keys, it would be enough if {[]} could be triggered by win+7890. 
So  I was playing a little with the xmodmap but I couldn't figure out how to to change the third level chooser for a specific key (7890 in this case).
I think it should be possible to get the behavior I want, because there are some shortcuts involving the windows key. The overview is only shown if the windows key is pressed and released again with no other key. But when you are pressing windows key + d for example - the desktop is shown.
I hope you understand my problem and can give me some hints how I can get the behavior I want, which is -> 
windows key press and release: overview as usual
windows key + 7 : { (third level of 7 on german keyboard) 
windows key + 8 : [ (third level of 8 on german keyboard) 
windows key + 9 : ] (third level of 9 on german keyboard) 
windows key + 0 : } (third level of 0 on german keyboard)


Thanks in advance

---

### Post by TxP on 2012-05-06
Hi,

I found now a solution which doesn't exactly produce the behavior I described in my initial post but with which I am very happy.
So I have now managed to map the third level chooser for {[]} on ctrl+7890 .
This is cool because I can press ctrl with the left hand and 7890 with the right hand. And the most important thing the other shortcuts involving ctrl are not affected by this. If I had simply selected the ctrl key to be third level chooser, all the copy, paste, cut stuff and so on, would not work anymore.

So this is how I did it:
The first thing you should do is download "xdotool" - its in the official sources.
Next you should navigate to Systemsettings -> Keyboard ->  Shortcuts -> Custom Shortcuts
Here you add a new shortcut (using the "+" button) give it a name you wish and as command you put in: xdotool key --clearmodifiers ISO_Level3_Shift+7
This will make the left curly bracket "{" on a german keyboard, which you get by pressing the third level chooser and 7.
Now you can map this command on the shortcut you wish - unfortunately the windows key doesn't work -  there seems to be some conflicts with the windows key as a trigger for the overview. That is the reason why my original idea of using the windows key doesn't work, but ctrl works great for me. The --clearmodifiers was important, at least on my machine, because otherwise the ctrl key gets interpreted as well and you end up with ctrl+ISO_Level3_Shift+7.

What is even cooler for programming is this setup here, which I am going to use:

ctrl+7:  xdotool key --clearmodifiers  ISO_Level3_Shift+7+0+Left
ctrl+8 : xdotool key --clearmodifiers ISO_Level3_Shift+8+9+Left



On a german keyboard ctrl+7 will give you {} with the cursor between the two brackets, which is really nice in programming for functions and classes.

ctrl+8 will do the same thing with the square brackets.

Have a nice day...

Edit: Should I flag the thread as solved? - I mean the original question isn't answered, nevertheless I am happy with this workaround ;-)

---

