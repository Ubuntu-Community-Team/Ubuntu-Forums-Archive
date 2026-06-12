---
title: "Face Recognition Security Software for Linux"
date: 2009-04-26
forum: General Help
---

### Post by Schok on 2009-04-26
I am using Banana Security which i got from this website [http://www.tinkernut.com/archives/682#socialize]("http://www.tinkernut.com/archives/682#socialize") for my xp and was wondering is there any free face recognition software similiar to this for linux?

Kubuntu 9.04 user(cant seem to find the edit button for my sig..)

---

### Post by mb_webguy on 2009-04-26
A quick Google search turned up a number of [projects in early development]("http://pages.cpsc.ucalgary.ca/~hanlen/vision/facelinks.html"), and a couple of [commercial systems]("http://www.filebuzz.com/findsoftware/linux_face/1.html") with price tags in the hundreds of dollars (presumably for enterprise-level applications).

Of course, you do know biometrics are a bit of a joke, and nowhere near as secure and reliable as a good password, right?  You can fool 2D facial recognition apps with a photograph.  Fingerprint scanners can be fooled by a piece of tape with a lifted fingerprint, or a piece of damp paper with a photocopy of the person's fingerprint.  Voice recognition software can be fooled by a digital voice recorder with a decent speaker.  

And all of them will fail due to normal bodily changes.  Gain or lose a few pounds, or wear a bit more or less makeup than usual, and the facial recognition software might not recognize your face.  Get a cut or burn on your finger, and the fingerprint scanner won't let you log in to your computer.  Catch a cold or laryngitis, and neither will voice recognition software.

On the other hand, if a password is at least eight characters, includes numbers and/or special characters, and is something you can easily remember, it will *always* work, and is very secure as long as you keep it in your head.

---

### Post by elliotn on 2009-04-26
> **mb_webguy said:**
> A quick Google search turned up a number of [projects in early development]("http://pages.cpsc.ucalgary.ca/~hanlen/vision/facelinks.html"), and a couple of [commercial systems]("http://www.filebuzz.com/findsoftware/linux_face/1.html") with price tags in the hundreds of dollars (presumably for enterprise-level applications).

Of course, you do know biometrics are a bit of a joke, and nowhere near as secure and reliable as a good password, right?  You can fool 2D facial recognition apps with a photograph.  Fingerprint scanners can be fooled by a piece of tape with a lifted fingerprint, or a piece of damp paper with a photocopy of the person's fingerprint.  Voice recognition software can be fooled by a digital voice recorder with a decent speaker.  

And all of them will fail due to normal bodily changes.  Gain or lose a few pounds, or wear a bit more or less makeup than usual, and the facial recognition software might not recognize your face.  Get a cut or burn on your finger, and the fingerprint scanner won't let you log in to your computer.  Catch a cold or laryngitis, and neither will voice recognition software.

On the other hand, if a password is at least eight characters, includes numbers and/or special characters, and is something you can easily remember, it will *always* work, and is very secure as long as you keep it in your head.


And thats the truth, imagine not being let in jst coz u had a hair cut

---

### Post by Schok on 2009-04-27
party pooper :(

lol nah jk..the software has an option to enter password in case it does not recognize you..and if im not mistaken everytime u enter the password it updates the face it saves..or you can just do it manually..it might not be as secure as an encryption, its just something cool to show off with ur busybodied mates..lol but thx for ur opinions btw

---

### Post by thisnamestoolong on 2009-05-06
That is a bummer -- I have an Asus laptop that came preloaded with **cough** Vista, and has a facial recognition login. It is most certainly less secure than a password, but I get up and down from my desk so frequently I have grown quite fond of the convenience of just having to look at my built in webcam to login. The benefits of Linux over Windows definitely negates that convenience though, I am very glad to have made the switch :P

---

### Post by zzzqzzz on 2010-07-26
Give it a try.
[http://code.google.com/p/pam-face-authentication/]("Give it a try. http://code.google.com/p/pam-face-authentication/")

---

### Post by drkages on 2010-08-07
> **mb_webguy said:**
> A quick Google search turned up a number of [projects in early development]("http://pages.cpsc.ucalgary.ca/~hanlen/vision/facelinks.html"), and a couple of [commercial systems]("http://www.filebuzz.com/findsoftware/linux_face/1.html") with price tags in the hundreds of dollars (presumably for enterprise-level applications).

Of course, you do know biometrics are a bit of a joke, and nowhere near as secure and reliable as a good password, right?  You can fool 2D facial recognition apps with a photograph.  Fingerprint scanners can be fooled by a piece of tape with a lifted fingerprint, or a piece of damp paper with a photocopy of the person's fingerprint.  Voice recognition software can be fooled by a digital voice recorder with a decent speaker.  

And all of them will fail due to normal bodily changes.  Gain or lose a few pounds, or wear a bit more or less makeup than usual, and the facial recognition software might not recognize your face.  Get a cut or burn on your finger, and the fingerprint scanner won't let you log in to your computer.  Catch a cold or laryngitis, and neither will voice recognition software.

On the other hand, if a password is at least eight characters, includes numbers and/or special characters, and is something you can easily remember, it will *always* work, and is very secure as long as you keep it in your head.

I do not believe that this is the best approach to thinking about the issue. Is one thing to raise the reality of the technology and its limitations then, and even now, but its another issue to give the impression that attempting to implement the technology in linux is pointless (not explicitly stated).

I think it should be encouraged and developments be made to fool-proof it with time and as technology on laptops, desktop (and now cell-phones) develop. So too should linux position itself to use these devices for security and authentication purposes.

I propose that those of us, who have laptops and fingerprint readers should look at avenues to lobby (IRC and mailing list) to ensure that pressure be placed on ensuring the desktop can allow modules for these technologies to be included for authentication (login and gksudo).

---

