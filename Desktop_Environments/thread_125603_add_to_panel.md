---
title: "add to panel?"
date: 2006-02-04
forum: Desktop Environments
---

### Post by ESPOiG on 2006-02-04
is there like plugins or sumtin that give us extra features to add to the panels??

just wondering after i deleted my main one today by accident and wen readding everything i thought maybe you can get extra ones :S

---

### Post by Perfect Storm on 2006-02-04
You mean installing extra applets to the main panel? Yes, but it depends what you're looking for.

I can recommend gxmms and Keyboard Lock Keys.

---

### Post by madmetal on 2006-02-04
is there other panels except for ubuntu standard?

---

### Post by Perfect Storm on 2006-02-04
You mean for gnome? The other desktop envoriments have their own panels.

But there's also fbpanel and pypanel (and properly some more)

---

### Post by madmetal on 2006-02-04
yes i am using gnome.
i am asking if i am able to have more options at the standard panel.
(other enviroments panels are better?)

---

### Post by Perfect Storm on 2006-02-04
Well it's actual a question about taste in my opinion. I'm really happy with gnome panel if you ask me.

---

### Post by madmetal on 2006-02-04
i am happy too! but its always good to ask and learn! :)

---

### Post by ESPOiG on 2006-02-04
how/where do u get the extra panel thingos

---

### Post by Schmic on 2006-02-05
I have been playing with my panel and applets aswell and would also like to know what other options there are?

I would actually like to remove the panel because i have been looking at panels for many years and am getting kinda sick of them bordered all the time and like the fact that you can remove them in ubuntu. I have a few small questions:

My first question is if i remove all the gnome panels how can i replace it again later?

How can you get the default panel from first install back appart from rebuilding it manually by adding the applets?

I am trying gdesklets to get some other options for panel replacements to show the details i want to see, is there any other apps that can do that for me to try/or work better?

ps. i am new to linux but love the fact that you can actually do these things to it. In my eye's it makes it far more superior to windoze :)

---

### Post by Perfect Storm on 2006-02-05
> My first question is if i remove all the gnome panels how can i replace it again later?

```
sudo apt-get install gnome-panel
``` if you mean remove it as in uninstall it. So you can apt-get it back.


> How can you get the default panel from first install back appart from rebuilding it manually by adding the applets?

command: gnome-panel
and you will get the default gnome panel back but without any applets so you have to add them again.
But again you might find config files somewhere in your /home/<username>/ which have the information on how your panel is setup, if you find them make sure to back them up before removing gnome panel.

> I am trying gdesklets to get some other options for panel replacements to show the details i want to see, is there any other apps that can do that for me to try/or work better?

adesklets, conky, gkrellm and perhaps superkaramba but I have heard it doesn't work so good in a gnome desktop as it's a KDE thing.

---

### Post by Perfect Storm on 2006-02-05
[QUOTE=ESPOiG]how/where do u get the extra panel thingos[/QUOTE]

Normally through apt-get just make sure to setup your sourcelist with universe and multiverse. If it aren't there too you might to compile it from the source. But last I checked they are in the sourecelist.

---

### Post by Schmic on 2006-02-05
ty Artificial Intellligence, now i know i can get the panel back so easily i feal comfortable removing it until i decide i want it back again. I'll look into the other alternatives too. I appreciate the feedback

edit: tried to delete the last panel but it won't let me saying <error   cannot remove last panel> any suggestions?

---

### Post by Schmic on 2006-02-22
Got my desktop sorted out the way i liked it and uninstalled gnome-panel to try and stop it covering the open windows. Unfortunately G-desklets gnomebar must rely on it because i lost few of the functions on it such as the windows list :( .

Any other suggestions or will i just have to put up with the gnome-panel?

---

