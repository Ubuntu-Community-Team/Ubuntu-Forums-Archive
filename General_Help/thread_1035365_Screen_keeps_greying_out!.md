---
title: "Screen keeps greying out!"
date: 2009-01-09
forum: General Help
---

### Post by casmok on 2009-01-09
From time to time when I'm in Firefox the page slowly fades its colours and go's grey and then returns back to colour again/ The whole fade out cycle usually lasts about 2 or 3 seconds, occasionally a bit longer. This is not happening every time and seems to vary according to the web page I on.

Any ideas? I'm wondering if its a memory problem?

The other thing which may/may not have something to with the above is when I'm NOT using Firefox and just have some application open and I open another window the rest of the desktop will go grey. E.G. If I open Add/Remove programs and decide to add something when the box asking me confirm pops up the backgorund and desktop goes grey. when the download is complete and I closes it comes back to colour. This is an instantaneous change when I click. Is this normal?

Any ideas on the above appreciated
Thanks
Mike

Running Hardy 8.04
Compaq Presario M2000 laptop
AMD Turion 64
1GB RAM

---

### Post by namdung on 2009-01-09
Welcome to UbuntuForums. This being ur first post we'll definitely try to resolve ur issue.

When any application greys out, it just means that it is processing at the background. This usually lasts a few seconds. If a particular application is causing this issue regularly, monitor its process in *System==>Admin==>System Monitor==>Processes*. U may kill any unwanted applications and give more priority to the particular application.

---

### Post by casmok on 2009-01-09
> **namdung said:**
> Welcome to UbuntuForums. This being ur first post we'll definitely try to resolve ur issue.

When any application greys out, it just means that it is processing at the background. This usually lasts a few seconds. If a particular application is causing this issue regularly, monitor its process in *System==>Admin==>System Monitor==>Processes*. U may kill any unwanted applications and give more priority to the particular application.

Hi 
Thanks for your reply! 

So e.g. when I open up System Monitor the coloured bar at the top of Firefox (with minimize/maximize/close etc) goes to grey. 
You are saying this is completely normal??


And what about when the colour just fades to grey at random and then come back 2 or 4 seconds later?

There are so many apps in sytem monitor, how do I know which I can safely kill?

Thanks
Mike

---

### Post by casmok on 2009-01-10
The other thing that sometimes happens when the colours fade out to grey is that my scrolling freezes. So in my mind its a memory problem of some sort?
What do you think?
Mike

---

### Post by Crafty Kisses on 2009-01-10
While Firefox is running, run the following command in Terminal:
```
top
```
Please post the results back here.

---

### Post by Cherylita on 2009-01-10
Hi, 
I just downloaded Ubunto 8.1 from 8.04 and am finding the same thing as Mike/Casmok. This was not happening as frequently in Hardy Heron..!
I went to CompizConfig Settings Manager and it show such things as Fade to Desktop and Fading Windows.  Are these where I should be changing settings to stop the fade?  I only have 2 tabs open when the fade is happening and it is happening 4 or 5 times during 10 minutes, but is not happening at all now that I am in Forum....Hmmmm are you recruiting all new members to Forums?  Is this a conspiracy? ;)
Thanks for your time!
Cherylita

---

