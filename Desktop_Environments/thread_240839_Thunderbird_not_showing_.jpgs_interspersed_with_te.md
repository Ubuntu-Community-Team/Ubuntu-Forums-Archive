---
title: "Thunderbird not showing .jpgs interspersed with text"
date: 2006-08-21
forum: Desktop Environments
---

### Post by jimbob on 2006-08-21
In mozilla-thunderbird an email with multiple *.jpg attachments will only display with empty boxes interspersed with the text instead of displaying the .jpgs inline where they should be.

I can look at the jpgs separately if I want but how do I make them appear in with the main email where they should be?
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by Paul41 on 2006-08-21
At the top right above the message there should be a button that says something like "Show Images" (I am at my work computer which does not have Thunderbird so I can't remember exactly what it says).  If you click that button the images will show up in you message.

---

### Post by jimbob on 2006-08-21
Thanks, but I have looked all over and cannot find anyplace where I can select "display images"
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by Paul41 on 2006-08-21
Look at the first screenshot link here.  It shows where the button normally is.
[http://kb.mozillazine.org/Privacy_basics_(Thunderbird](http://kb.mozillazine.org/Privacy_basics_(Thunderbird))

---

### Post by jimbob on 2006-08-21
OK, I'm thoroughly confused.

First of all I do not have a message bar like that in T-bird.

No matter what I do I cannot make it come up even by disallowing HTML and sending a message containing some.

Regarding the email that won't work, I forwarded it to myself at gmail and it worked perfectly there.

So I then sent it back to myself at T-bird and now it works there but the original one still won't.

Then I turned off HTML in T-bird and sent it again from gmail and it failed as expected but I still never got that bar that says "show images" ???

Go figure, I give up.](*,) 

Thanks for your help.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by KrIaXPaTaLa on 2007-11-01
I think I may have your same problem. Some mails I receive do not show the images inline, both in linux as in windows. It has nothing to do with allowing or not images, because the sender is on my address book. Plus, thunderbird itself does not give me the option 'Show Images'. So, whats happening?

It seems like thunderbird is not detecting the jpg files as images. However, if I choose to open each file individualy, it will popup image viewer as the default app to deal with the file. So the attachments are OK, but they still do not apear in the message body.

Turns out, theres a tag on the mail source code: **Content-Type**.

This tag tells TB what is the type of the next section on the e-mail. Unfortunatly, without reason I know of, ppl are aparetly sending me e-mails with errors on the source code, because I stoped having **Content-Type: image/jpeg** on the embebed images, and all I have now is  **Content-Type: unknown/unknown**. This seems enough to confuse TB, but not Outlook Express, for example, so I suspect this is another form of mirco$hit trash on html edition.

What I'me still trying to garantee is that the e-mails are sent with this exact same code, and that it's not my client thats changing it (highly douthful).

Could I be right? Is the Content-Type the problem? Can this be 'solved' in some way?

Regards.

---

