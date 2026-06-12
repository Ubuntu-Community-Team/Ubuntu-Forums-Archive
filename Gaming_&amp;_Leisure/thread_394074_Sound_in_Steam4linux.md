---
title: "Sound in Steam4linux"
date: 2007-03-26
forum: Gaming &amp; Leisure
---

### Post by MonkeyBoy on 2007-03-26
I installed steam4linux yesterday and activated my old halflife key.  Everything was great but today when i booted it up there is no sound.  Here is the output of the terminal that i think is relevant.  

err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
err:dsound:DSOUND_MixOne underrun on sound buffer 0x1eed38

It is a mystery why this is happening.  It seems to affect Thinktanks too but not NWN or Sauerbraten.

Any suggestions?

---

### Post by MonkeyBoy on 2007-03-26
> I installed steam4linux yesterday and activated my old halflife key. Everything was great but today when i booted it up there is no sound. Here is the output of the terminal that i think is relevant.

```
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
err:dsoundSOUND_MixOne underrun on sound buffer 0x1eed38
```

It is a mystery why this is happening. It seems to affect Thinktanks too but not NWN or Sauerbraten.

Any suggestions?

Sorry about the rogue smiley...I should press "preview" more often.

---

### Post by Brynster on 2007-03-27
run ```
Winecfg
``` in terminal.

select the sound tab and try differing sound ioptions

---

### Post by MonkeyBoy on 2007-03-27
Well I've monkeyed with the wine audio stuff a bit but no change.  Does Steam4linux run under wine?  I didn't use wine to install it.

This is particularly annoying 'cos i tried it again this morning and the sound was OK but now I'm home again it is gone.

---

### Post by Brynster on 2007-03-28
steam4linux unless i am wrong is an automated install of of wine and steam rolled into one package.

To the best of my knowledge (and i have tried it several times) steam4linux isn't as effective as doing a pure wine install and then installing steam et al. It used to be very effective at "fixing" the 26% update bug, but that hasn't been an issue in wine since around 0.9.26, simply restart wine when/if it hangs at 26% on the update.

There is a a website for steam4linux which does (did) have a contacts detaisl for the author of that package although i don't think English is his/her native tongue. (Sorry i know that sounds really conceited and assuming that the world speaks English it wasn't intended that way). Give them a try they may be able to help further.

---

### Post by MonkeyBoy on 2007-03-28
Thanks.  That makes sense.  as it seems to work sporadically I will stick with it for now and switch to a pure wine install on Feisty when I upgrade.  I might try a different soundcard too.

---

### Post by arhwebmaster on 2007-05-21
> **Brynster said:**
> steam4linux unless i am wrong is an automated install of of wine and steam rolled into one package.

To the best of my knowledge (and i have tried it several times) steam4linux isn't as effective as doing a pure wine install and then installing steam et al. It used to be very effective at "fixing" the 26% update bug, but that hasn't been an issue in wine since around 0.9.26, simply restart wine when/if it hangs at 26% on the update.

There is a a website for steam4linux which does (did) have a contacts detaisl for the author of that package although i don't think English is his/her native tongue. (Sorry i know that sounds really conceited and assuming that the world speaks English it wasn't intended that way). Give them a try they may be able to help further.

Yes . You're right. My name is Anders Rytter Hansen . It's me who has made Steam4linux, and my native language is Danish. I know that I've made some errors about the translation from Danish to english in the installation of Steam4linux, and I am better in English now. I will use "my try", as you gave to a better translation . :D .

---

