---
title: "how to save images in evolution html emails"
date: 2006-01-02
forum: Desktop Environments
---

### Post by DSab on 2006-01-02
Hello,

About evolution 2.4.1, does anyone know how to save images received embedded as mime parts in HTML messages? I receive many HTML mails like that (from outlook mailers), and I would like to save these images in their original format (gif or jpg) on my disk.

It may be very simple, but I can't find the way... I only manage to save attachments, not embedded parts.

Thanks.

---

### Post by DSab on 2006-01-03
Again, does anybody has a clue about saving images received in html emails in evolution 2.4.1?

---

### Post by gw90se on 2006-01-03
If I read this right, open Nautilus. Make sure it is set to show hidden files. Browse to .evolution/cache/http. You will see several folders such as 00, 0a, etc. Look through these and you will find the image.

---

### Post by Herman on 2006-01-03
I tried and the only thing I found that would work was, oddly enough, was to send the whole e-mail to hotmail. Then, I can right-click on it and get an option for 'save image as', on the right-click menu! That's one way.
When mail it back to myself from hotmail, it comes back as an attachment, and I can also save that. That's another way.
But I couldn't copy the image directly off an e-mail either.
(Herman)

---

### Post by DSab on 2006-01-03
[QUOTE=gw90se]If I read this right, open Nautilus. Make sure it is set to show hidden files. Browse to .evolution/cache/http. You will see several folders such as 00, 0a, etc. Look through these and you will find the image.[/QUOTE]

Mm,  doesn't seem to work. I don't have a .evolution/cache/http directory, I do have something like .evolution/mail/pop/ptxxx-yy@pop.1and1.fr/cache/, but the subdirectories do not contain any readable image even though evolution is currently displaying the right email.

Following the idea, I displayed the image and then typed 'find . -mmin -3 -print' to display all modified files in the last 3 minutes, in my home directory and in /tmp. Nothing looking as a image, even without filename extention. So I suspect that evolution uudecodes the images and display it on the fly, without the disk.

Thanks for the idea anyway.

---

### Post by DSab on 2006-01-03
[QUOTE=Herman]I tried and the only thing I found that would work was, oddly enough, was to send the whole e-mail to hotmail.
(Herman)[/QUOTE]

Good idea, this works for sure as it is always possible to save images in a browser.

Anyway, I find strange that the creators of evolution did not embedded a direct way to do that...

---

### Post by golem3 on 2006-12-13
> **Herman said:**
> I tried and the only thing I found that would work was, oddly enough, was to send the whole e-mail to hotmail. Then, I can right-click on it and get an option for 'save image as', on the right-click menu! That's one way.
When mail it back to myself from hotmail, it comes back as an attachment, and I can also save that. That's another way.
But I couldn't copy the image directly off an e-mail either.
(Herman)

GRRR...it's very annoying, isn't it? I just love open source, and all it philosophy, but you have to hand it for the evils of Microsoft...they pool their heads into one product, so all the features are there (regardless of how terrible and slow Outlook is)

BTW - I would never switch back to Windows. Sorry to go off topic. If anyone can figure out a plugin to get images to save, that would be great!

---

