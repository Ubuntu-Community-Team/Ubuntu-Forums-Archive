---
title: "Registration page on .com has broken CAPTCHA preventing registration of new"
date: 2008-06-05
forum: Forum Feedback &amp; Help
---

### Post by sdiamond on 2008-06-05
I wasn't able to register as a new user on the ubuntu forums because the captcha image didn't show when the .com TLD was used rather than .org.

To see the problem do the following:

1) First log out of ubuntu forum and then go to
[http://search.ubuntuforums.com/register.php]("http://search.ubuntuforums.com/register.php")

2) Then click that you agree with the forum terms and the next screen you will see that the captcha image is replaced with the following error message.
[INDENT]Image Verification
This reCAPTCHA key isn't authorized for the given domain. More info [/INDENT]

The registration form works fine if you happen to be on the .org url rather than .com

Hopefully this can be easily fixed.

---

### Post by LaRoza on 2008-06-05
The only uri for UbuntuForums.org is: [http://ubuntuforums.org](http://ubuntuforums.org)

Although other domains were obtained to prevent phishing, this is the only domain (except for the LoCo forums and such) to use.

Use ubuntuforums.org only.

---

### Post by haz2a on 2008-07-07
Its only solved for searchers that persist and find this page!
Also, I had this from the forum Search page, when I was already loggod-on as a user, not trying to register.

Something should be done about this - it must be a real user-loser.

How many new users, coming to the forums because they are having problems with ubuntu, then find that they can't get the forum site to work either. They can spend as long as they like checking and re-checking their browser settings and re-trying the search, even go to a different computer and still get exactly the same problem with no clues that problem is with the URL. This sort of thin gets people very angry and frustrated. How many newbies curse ubuntu and never come back?

I ended up on the .com domain after a Google search. My bookmarks are .org.

Can't the non-functional domains at least put up a message telling searchers to use the .org domain?

---

### Post by -grubby on 2008-07-07
> **haz2a said:**
> 
Can't the non-functional domains at least put up a message telling searchers to use the .org domain?

Actually, I think redirecting would make alot more since than mirroring the site..

---

### Post by zalg on 2008-07-09
I just registered for my account at [http://ubuntuforums.org/register.php?do=register](http://ubuntuforums.org/register.php?do=register) and it took a lot of tries before the captcha image appeared

The captcha imaged returned the following errors (instead of the image):

convert: unable to read font `/srv/www.ubuntuforums.org/public_html/images/regimage/fonts/._SPONGY.ttf'.

convert: unable to read font `/srv/www.ubuntuforums.org/public_html/images/regimage/fonts/._WetPet.ttf'.

convert: Not a JPEG file: starts with 0x00 0x05 `/srv/www.ubuntuforums.org/public_html/images/regimage/backgrounds/._background9.jpg'.

convert: Not a JPEG file: starts with 0x00 0x05 `/srv/www.ubuntuforums.org/public_html/images/regimage/backgrounds/._background7.jpg'.

After refreshing the captcha image about 15 times it hit a correct font and a correct background....

I thought I'd mention it here because I doubt anyone managing the forum registers a new user frequently ;-)

---

### Post by jpeddicord on 2008-07-09
> **zalg said:**
> I just registered for my account at [http://ubuntuforums.org/register.php?do=register](http://ubuntuforums.org/register.php?do=register) and it took a lot of tries before the captcha image appeared

The captcha imaged returned the following errors (instead of the image):

convert: unable to read font `/srv/www.ubuntuforums.org/public_html/images/regimage/fonts/._SPONGY.ttf'.

convert: unable to read font `/srv/www.ubuntuforums.org/public_html/images/regimage/fonts/._WetPet.ttf'.

convert: Not a JPEG file: starts with 0x00 0x05 `/srv/www.ubuntuforums.org/public_html/images/regimage/backgrounds/._background9.jpg'.

convert: Not a JPEG file: starts with 0x00 0x05 `/srv/www.ubuntuforums.org/public_html/images/regimage/backgrounds/._background7.jpg'.

After refreshing the captcha image about 15 times it hit a correct font and a correct background....

I thought I'd mention it here because I doubt anyone managing the forum registers a new user frequently ;-)

Yuck, that's a nasty error. I've brought this to the attention of the admins.

---

### Post by scootre on 2008-07-20
Browser + platform issue perhaps?

I've just joined and I could not see the CAPTCHA image in Firefox 3 under Ubuntu 8.04, no matter how many times I reloaded the page.

Switching to XP, it works every time in Firefox 2.  Haven't loaded Firefox 3 on XP yet to know it it is purely a FF3 problem.

---

