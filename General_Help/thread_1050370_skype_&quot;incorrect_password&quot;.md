---
title: "skype &quot;incorrect password&quot;"
date: 2009-01-25
forum: General Help
---

### Post by bkbk on 2009-01-25
With Ubuntu 8.10, I downloaded Skype from the Medibuntu repository, but I can't sign into Skype. It always says, "Incorrect Password." I can sign into my account at skype.com, so I know I have the password correct.

This is Skype version 2.0.0.72. According to Synaptic, I've installed skype and skype-common, but not skype-static, skype-static-oss, or skytools.

Thanks in advance for any help you can provide.

---

### Post by jespdj on 2009-01-25
Are you copying and pasting the password from somewhere into Skype? That doesn't work with Skype - it will say that the password is wrong. Carefully type it yourself.

And ofcourse check if your caps lock is not on, or try typing it into a text editor, to see if your keyboard isn't set to some other keymap than you think.

---

### Post by bkbk on 2009-01-25
I'm typing it correctly.

---

### Post by bkbk on 2009-01-26
Someone on a Skype forum gave some advice that worked:

I renamed the .Skype folder in my home directory, opened Skype, then logged in --- and it worked! Then I deleted the renamed .Skype directory, since Skype had created a new one.

---

