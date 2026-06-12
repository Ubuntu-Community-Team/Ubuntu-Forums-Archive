---
title: "Language for Skype 4.0 in XFCE 4.10"
date: 2012-06-30
forum: Desktop Environments
---

### Post by new-to-ubuntoo on 2012-06-30
Hi Fellow Users,

Im having an issue with Skype. I just recently updated to XFCE 4.10 then updated my Skype to 4.0XXXX whatever. The languages seem to be all messed up now.

I have tried changing it to English on my options page under XFCE and restart Skype but it does change the language no matter what i pick.

If I use Unity Desktop the language is fine and all in english.  Does anyone know how to fix this. I have looked around the web but couldnt find much. I cant seem to get a screen shot of the options page in the foreign language. I only have english languages installed on the system.

Thanks

Ubuntu User

---

### Post by mexicanseaf00d on 2012-06-30
you could try and remove your .Skype folder in your Homedir. Settings are stored there and there may be some incompatibilities.

open your Filemanager, hit **CTRL+H** to view hidden files and rename **.Skype** to something else. Start skype and try to set your options

---

### Post by new-to-ubuntoo on 2012-06-30
Unfortunately, that does not work. it seems to reset all my settings. I select the english language on start up but then it doesnt actually change it to english.

i managed to get a screenshot now.

---

### Post by mexicanseaf00d on 2012-06-30
Did you change the font in xfce?

Try to set it to ubuntu for example in xfce settings

You could also have a look at "shared.xml" file in the .Skype folder - near the bottom you see Options for Language (should be "en") and also appearance

try and set "GTK+" without the quotationmarks in  <Style>. the bottom of my config looks like this, for example:

```
 <UI>
    <Installed>2</Installed>
    <Language>de</Language>
    <Pos>
      <Height>313</Height>
      <Width>276</Width>
      <X>1316</X>
      <Y>372</Y>
    </Pos>
    <SavePassword>1</SavePassword>
    <StartMinimized>1</StartMinimized>
    <Style>GTK+</Style>
  </UI>
```

default is <Style>Desktop Settings</Style>

---

### Post by new-to-ubuntoo on 2012-06-30
Thankyou,

You helped my problem. I also changed the font, background and theme when i upgraded to give my computer a "fresh" feel.

I changed the font to "symbol" which is what the problem was. I have changed the font again and now skype is showing english again.

I do think its a little strange that the rest of my computer was having no issues with the font selection but skype did.

anyways maybe when i upgrade i should do things more slowly so i can have a better idea of what actually caused the problem.

thanks

---

### Post by mexicanseaf00d on 2012-06-30
cool

---

