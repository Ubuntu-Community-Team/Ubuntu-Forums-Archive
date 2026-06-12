---
title: "Black screen on any game using nvidia driver"
date: 2014-05-03
forum: Gaming &amp; Leisure
---

### Post by pettrus.sherlock on 2014-05-03
I don't know if i am posting on the right place but my problem is related to games.

My problem is:if i try to play ANY game i get a black screen(actually my monitor says there is no signal and turn off) and i keep listening to the music in the back ground, first i thought was a steam problem, because i can do anything(watch youtube and movies full screen and even play some browser games),  without a problem with the nvidia driver except play games, but then i tried Strife i launched strife and got the black screen on the login screen! is not even full screen! but i can run the Strife updatemanager without any problem! But i can play many of the software central games smoothly.

[COLOR=#333333][FONT=UbuntuRegular]I have a [/FONT][/COLOR]geforce gt 630(I am using a DVI to VGA adapter)[COLOR=#333333][FONT=UbuntuRegular] and Ubuntu 14.04. I installed the nvidia driver using everyway possible, i tried addional drivers section, i tried using terminal but i still have the same problem, i also tried all the types of option that nvidia offers(binary, legacy, proprietary, open source blabla bla).

If i play using the nouveau driver the game runs normal, the only reason i am not using the nouveau driver right now its because when i am on eclipse looks like i am typing on a old overloaded pc, if i type 'a' takes half second to show on the screen.

Please i really need help, i can't stop programming but i can't stop playing game either and i don't wanna dual boot windows :(

[/FONT][/COLOR]

---

### Post by liz-alice on 2014-05-03
Glad to know I am not the only one having this problem. Thank you for pointing out the invidia drivers. I was wondering why some games worked and others didn't. I will be watching this thread to see what comes up. Thanks for asking the question, this is just the info I came here for. :)

---

### Post by MikeCyber on 2014-05-05
Make sure to have only those installed with synaptic.
-nvidia-settings
-nvidia-331

It works fine for my GTX770. Maybe you need another version but make 
sure to not have multiple installed.

PS: I also think the other 331updates package is broken

---

### Post by pettrus.sherlock on 2014-05-05
> **MikeCyber said:**
> Make sure to have only those installed with synaptic.
-nvidia-settings
-nvidia-331

It works fine for my GTX770. Maybe you need another version but make 
sure to not have multiple installed.

PS: I also think the other 331updates package is broken

It is not the driver, i tried others drivers and got the same problem, its problably some incompatibility with my monitor, because with nouveau drivers i can run ok, i would dare to say the fix to the problem is problably on the xorg.conf and i would have to add something to accept my monitor when trying to play games.

---

