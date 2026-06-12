---
title: "Multiple sounds"
date: 2006-08-19
forum: Desktop Environments
---

### Post by Emanuel Felipe on 2006-08-19
Hi..

I have follow some howtos here to make ubuntu play multiple sounds using alsa, works with players... but not with firefox/swiftfox flash.

So... I need to close my player after open firefox/swiftfox if I want to hear a flash with sound, and the players works again only if I close firefox/swiftfox.

And the Same happens with audacity... but this isnt a big problem... I think I dont want to hear music when editing audio...

If someone could help me.. thanks

---

### Post by Emanuel Felipe on 2006-08-19
anyone? :neutral:

---

### Post by galileon on 2006-09-01
hello,
i had the same prob, couldnt get audacity to record sound from a flash player in firefox...(although i got this precise thing to work two months back, but i dont remember how)...

my workaround is to install firefox for windoze in wine, ie download FirefoxSetup.exe into your home directory, open a console:

$ wine FirefoxSetup.exe

$ audacity&      <----------------this opens audacity first, which seems to be required

remember to set the litle button for recording to 'Vol', instead of 'mic'


$ wine ./.wine/drive_c/Program\ Files/Mozilla\ Firefox/firefox.exe

now you can browse to your flash-page, click record in audacity...

hope this helps, if i ever get the normal linux firefox to work with it ill post, bye.

---

