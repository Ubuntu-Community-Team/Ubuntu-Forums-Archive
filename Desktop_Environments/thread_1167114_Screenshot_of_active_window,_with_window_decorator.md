---
title: "Screenshot of active window, with window decorator emerald?"
date: 2009-05-22
forum: Desktop Environments
---

### Post by mk__ on 2009-05-22
Hi, ubuntuforums.org…

I'm looking for a screenshot tool — able to take screenshot of the active window, with the window decorator (Emerald.)

As far as i can tell, ImageMagick does not support that, which is a huge problem.. Although scrot does — so that's what I was trying to use.

But it seems to have no active—window—only support, do you know any screenshot tools which has, or does scrot have a method to do it?

Thanks,
sincerely — mk.

---

### Post by gettinoriginal on 2009-05-22
I must not understand what you are asking for, as Applications > Accessories > take screen shot has always worked for me.  :p
Sample
[ATTACH]114675[/ATTACH]

---

### Post by mk__ on 2009-05-22
> **gettinoriginal said:**
> I must not understand what you are asking for, as Applications > Accessories > take screen shot has always worked for me.  :p
Sample
[ATTACH]114675[/ATTACH]

Yes, thank you — i know that.

But the problem is that I'm supposed to use this with a hotkey (using xbindkeys which launches a script.)

The scrot --select argument is not functional from xbindkeys (I have no idea why, actually, maybe i should fill this in as a bug?)

Or maybe — is it possible to save the screenshot without the GUI dialog?

Thanks,
sincerely — mk.

---

### Post by gettinoriginal on 2009-05-22
Sorry, I don't anything about scrot, but I did find this.  Sorry if you already checked it.
[https://help.ubuntu.com/community/scrot]("https://help.ubuntu.com/community/scrot")

---

### Post by mk__ on 2009-05-22
I already knew that — it's the man page for scrot

but, thanks.
sincerely — mk.

---

### Post by mk__ on 2009-05-23
Bump - no solution?

---

### Post by kaibob on 2009-05-23
Imagemagick has the ability to make a screenshot of an active window, although, as with scrot, you have to click on the window. The simple command is:

```
import -frame filename.png
```

I have placed this command in a shell script and assigned it to a keyboard key. It works fine. I don't use Emerald, so I don't know if this would be an issue.

---

### Post by mk__ on 2009-05-23
> **kaibob said:**
> Imagemagick has the ability to make a screenshot of an active window, although, as with scrot, you have to click on the window. The simple command is:

```
import -frame filename.png
```

I have placed this command in a shell script and assigned it to a keyboard key. It works fine. I don't use Emerald, so I don't know if this would be an issue.

I suggest you to read the OP before posting...
> I'm looking for a screenshot tool &#8212; able to take screenshot of the active window, with the window decorator (Emerald.)

**As far as i can tell, ImageMagick does not support that**, which is a huge problem.. Although scrot does &#8212; so that's what I was trying to use.

---

### Post by kaibob on 2009-05-23
Post deleted by kaibob.

---

