---
title: "Thunderbird mail"
date: 2018-08-19
forum: Desktop Environments
---

### Post by jhboards on 2018-08-19
After recent Ubuntu updates, my Thunderbird Mail server setting were corrupted. I am trying to verify my TB password on 1 account but I cannot find the TB password page. It used to be [Ubuntu TB] Edit > Preferences > Security but now there is no password area/option. Ideas please.

---

### Post by lisati on 2018-08-19
I see what you mean. I had a look around Edit->Account Settings as well and couldn't see a place to save passwords there either.

When I have issues logging into an email account with Thunderbird, a dialog box sometimes pops up and usually gives me an option to enter a "New" password.

---

### Post by jhboards on 2018-08-19
Mine does pop up too, but does not work or save it. And for the record, the [Ubuntu]Firefox security does not host the em passwords.

---

### Post by jhboards on 2018-08-19
Fixed. 

Who designed this interface??? You have to click on the word "*_**passwords**_*" in the upper line "***Junk E-mail Scams Antivirus** **Passwords***", THEN the "***saved passwords***" option displays. There is no "tab" or other way to see that these are clickable links. Just a string of words that [to me] appear to be a title bar.

The same update that turned this off by default also changed my TB Gmail accounts outgoing server settings from "***normal password***" to "***0auth2***" authentication method and also changed the passwords to long, random strings. WTF? This is getting to be Like Windows, where the "updates" disable or blow out the screen saver and other settings. Ugh!

_**Here is what I could not see before:**_


[ATTACH=CONFIG]280790[/ATTACH]

---

### Post by walts48 on 2018-08-20
What version of Thunderbird?

I'm having no problems with Ubuntu's build of Thunderbird 52.9.1.

That interface has been in place for many versions, designed by the Thunderbird developers.

Still waiting for the update to 60.0 which was released 2 weeks ago. Maintainer on vacation?

---

### Post by &amp;KyT$0P# on 2018-08-20
> **jhboards said:**
> You have to click on the word "*_**passwords**_*" in the upper line "***Junk E-mail Scams Antivirus** **Passwords***", THEN the "***saved passwords***" option displays. There is no "tab" or other way to see that these are clickable links. Just a string of words that [to me] appear to be a title bar.
They're supposed to be tabs.  I too have noticed that Mozilla-based GTK3 applications don't style tabs properly in Ubuntu 18.04.

As a workaround for this Mozilla/Thunderbird bug, you could use [userChrome.css]("http://kb.mozillazine.org/UserChrome.css") to implement some kind of visual indication of [FONT=Courier New]tab[/FONT] and [FONT=Courier New]tabpanel[/FONT] elements.

---

