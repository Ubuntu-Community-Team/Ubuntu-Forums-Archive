---
title: "Display problems"
date: 2011-04-01
forum: Desktop Environments
---

### Post by poodoopealeoaph on 2011-04-01
I have been using Kubuntu 10.04 and 10.10 and I have noticed some sort of a glitch on my systems. Sometimes when I am surfing the internet, writing a paper, or what have you, I experience that things aren't where they should be. To elaborate, when I try to click on a radio button, nothing will happen but if I move the mouse up or down an inch or two, I will see the icon to be able to click something. So, I click and the radio button is activated and has moved to where I just clicked. Another issue is that if i try to write an email, I will write one or two lines and then all of the following lines will seem to all be typed together on one line until I scroll down and back up to sort of reset the screen.... So, basically I love Kubuntu otherwise and I would really like to finally find a fix to this issue. I've searched for a fix for about a year now and haven't come across anything yet so... SOMEONE PLEASE HELP!! I'M TOO BORD WITH REGULAR UBUNTU, XUBUNTU IS BORING, AND LINUX MINT IS JUST... BLAH! Oh how I want to feel comfortable with KDE....

---

### Post by kio_http on 2011-04-02
This is a problem in kwin.

To fix this I would advice updating to kde 4.6.1 packages

Updating Packages

1. Add the Kubuntu PPA represitory
To learn how to add repositories in kubuntu click [here]("https://help.ubuntu.com/community/Repositories/Kubuntu").
The represitory you want to add is ```
ppa:kubuntu-ppa/backports
```
2. Open a terminal. To launch you can do ALT + F2 and type "konsole"

In konsole:
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

3. Restart the computer

Speeding up window management

1. In KDE system settings, go to Desktop effects.
Enable an effect call scale resize or something like that.
Set Crisp mode in the last tab of the setting page.

(If if is still slow)
2. Press ALT + F2 and type 
```
oxygen-settings
```
Disable some effects.

---

### Post by poodoopealeoaph on 2011-04-02
okay so I did as you said and I guess i'll have to check things out further to see if everything is working alright. Everything seems good so far though. The only thing that I am a little curious about is that the effect that said crisp effects and the effect before it, I couldn't find either effect. So, I'm just wondering if it may be named something different or if there is just a way to activate these effects through konsole.

---

### Post by poodoopealeoaph on 2011-04-02
Sorry to say that I'm still having the same problems... One big indicator that things are still acting up is when i go into the package kit and try to download updates or something else and the graphic where there is a hard drive with the boxes going into it is all blurred. It actually looks like wherever the boxes are on the screen that they just never go away.... down with KDE again possibly? i think so..

---

### Post by kio_http on 2011-04-03
Which graphic chipset does your computer have?

Temporarily, you can disable the desktop effects in system settings.

Is this problem reproduced on different computers?

---

### Post by poodoopealeoaph on 2011-04-04
for my graphics, I looked up the specs and all it told me is that it has "Intel® Graphics Media Accelerator 4500M". Also, yeah the same thing happens on both my desktop and my laptop.

the main thing that happens though is when you try to type in a text box like how you have to type to send a message on here. If I see where the text box is, it will look a little glitchey and when I click on things they won't be in their proper spots. It's almost like the page loads but the computer doesn't refresh where things should be. So, I get an old reading of where I should click and when I click there is nothing there or there is something there that shouldn't be there. Also, when trying to type in a text box, it can make the text look a little funny because it it showing it on a random part of the screen. I don't notice it as heavy as I used to in 10.04 and I'm still toying with 10.10 so I'm really hoping that this whole thing just gets resolved.... I could try your idea of turning off the desktop effects to see if it may just be that my computer can't handle it though.

---

### Post by kio_http on 2011-04-06
> **poodoopealeoaph said:**
>  I could try your idea of turning off the desktop effects to see if it may just be that my computer can't handle it though.

This graphic card should be able to handle it technically, however I tested a system with the exact same card and I have been able to reproduce the issue you have mentioned. I know about the problem you are describing and yes disabling desktop effects will solve it.
I guess the problem will vanish in later versions of kde to come.

In the meantime to solve this and keep desktop effects.

**Disable some of the desktop effects.**

Mainly stuff like animate on appear, minimize etc
In the general tab of desktop effects, enable only the various animations check-box.
Set up the advanced tab to look like the attached image.

**To use hardware acceleration on the titlebars**

Install crystal decoration style
```
sudo apt-get install kwin-style-crystal
```

Set up crystal in the Workspace appearance KDE settings.

**To have hardware accelerated UI elements.**

Create a folder somewhere in your user folder
Paste the attached .pl (unzip first) file in it.
```
cd /path/to/the/folder/you/created
```
```
sudo apt-get install build-essential cmake kdelibs5-dev kdebase-workspace-dev libxrender-dev libx11-dev git

```
```
perl oxygen-setup.pl
```
When the process completes
```
cd build
```
```
sudo make install
```

Enable the "Blur" effect in Desktop effects.
Now go in Application Appearance Settings and chose widget style "Oxygen Transparent"
Click the configure button and set the transparent slider like the one on my attachment.
Note: If you do not like transparency on UI elements, set a very minute amount of transparency but to not make the slider be on the opaque end, otherwise it will not use hardware acceleration.

Good Luck

---

### Post by poodoopealeoaph on 2011-04-14
I went through and disabled everything besides like two desktop effects. I just kept enough so that the panel at the bottom would still be clear and so when I hit the K button, I still get the smooth "slide up" action. After doing that though, I still had problems with visuals.... Sadly I think I'm going to be stepping away from Kubuntu until I get a new computer that completely rapes so i know for sure that I won't have any issues like this.

---

