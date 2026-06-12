---
title: "Image-only CAPTCHA conflicts with Ubuntu's declared accessibility goals"
date: 2007-09-08
forum: Forum Feedback &amp; Help
---

### Post by benjaminhawkeslewis on 2007-09-08
First, thanks to "Paladine" and "PriceChild" for pointing me in the direction of this forum.

One of the stated aims of the Ubuntu project is "to make Ubuntu, and its derivatives, usable by as many people as possible across ages, languages and physical abilities":

[http://www.ubuntu.com/products/whatisubuntu/accessibility](http://www.ubuntu.com/products/whatisubuntu/accessibility)

The Ubuntu Forums are an important support option for Ubuntu:

[http://www.ubuntu.com/support](http://www.ubuntu.com/support)

Indeed, users are often directed to search the forums before using other support options.

The forums include an "Accessibility Discussions" forum:

[http://ubuntuforums.org/forumdisplay.php?f=145](http://ubuntuforums.org/forumdisplay.php?f=145)

It's recommended by the Accessibility wikipage:

[https://wiki.ubuntu.com/Accessibility](https://wiki.ubuntu.com/Accessibility)

Contrary to one suggestion made on IRC, the fact that the HTML used by vBulletin forums is not ideal does not mean the forums are unusable with assistive technology. Such software and its users have to adapt to bad websites all the time.

However, the Ubuntu forum team have introduced a significant and unnecessary accessibility barrier to posting to the forums by *choosing* to enable the vBulletin visual CAPTCHA to inhibit registration and by requiring registration to contact an admin.

The accessibility problems of image-only CAPTCHAs, and their fundamental unacceptability to people with visual impairments, are notorious:

[http://www.w3.org/TR/turingtest/](http://www.w3.org/TR/turingtest/)

[http://www.456bereastreet.com/archive/200512/captcha_is_bad_for_accessibility/](http://www.456bereastreet.com/archive/200512/captcha_is_bad_for_accessibility/)

[http://www.captcha.net/](http://www.captcha.net/)

[http://www.afb.org/Section.asp?SectionID=57&TopicID=167&DocumentID=3153](http://www.afb.org/Section.asp?SectionID=57&TopicID=167&DocumentID=3153)

[http://www.nfb.org/nfb/NewsBot.asp?MODE=VIEW&ID=51&SnID=2](http://www.nfb.org/nfb/NewsBot.asp?MODE=VIEW&ID=51&SnID=2)

vBulletin allows you to enable visual CAPTCHA and set its difficulty level:

[http://www.vbulletin.com/docs/html/main/vboptions_group_register](http://www.vbulletin.com/docs/html/main/vboptions_group_register)

[http://www.vbulletin.com/docs/html/main/vboptions_image_settings](http://www.vbulletin.com/docs/html/main/vboptions_image_settings)

However, the developers clearly didn't envisage this being the *only* way to register, since vBulletin also has provision for adding users manually:

[http://www.vbulletin.com/docs/html/main/users_add](http://www.vbulletin.com/docs/html/main/users_add)

If you look at what vBulletin do themselves, while they do use their visual CAPTCHA on their forum, they also make it easy to find their email address:

[http://www.vbulletin.com/contact.php](http://www.vbulletin.com/contact.php)

By contrast, the Ubuntu forum team have compounded the problems of the visual CAPTCHA by *choosing* not to provide any obvious way to contact an admin without registering.

The CAPTCHA project (who created CAPTCHAs in the first place) stress that CAPTCHA implementations must be accessible, and that most CAPTCHA implementations are both insecure and inaccessible. They recommend using their own reCAPTCHA, which includes an audio alternative for the visually impaired. reCAPTCHA is not a *sufficient* solution, since it still excludes deafblind users, but it would be a vast improvement over vBulletin's CAPTCHA. As there is already a reCAPTCHA plugin for vBulletin, the forums team should considering using it in place of vBulletin's native CAPTCHA:

[http://www.vbulletin.org/forum/showthread.php?t=151824](http://www.vbulletin.org/forum/showthread.php?t=151824)

One way to cater for deafblind users too might be to combine the reCAPTCHA plugin with something like the question-and-answer-based NoSPAM CAPTCHA plugin:

[http://www.vbulletin.org/forum/showthread.php?t=124828](http://www.vbulletin.org/forum/showthread.php?t=124828)

I don't know enough about the vBulletin plugin system to able to say how feasible it would be to combine two plugins in this way.

The other easy option is to link from the main registration form to a contact form including all the information required for registration with which deafblind users (and others who cannot use the CAPTCHA, for example,  if they are operating from a console-only installation) could register. 

If necessary, this could be safeguarded from run-of-the-mill spambots by a question-and-answer CAPTCHA similar to NoSPAM. The questions should be relatively simple so as to mimimize the exclusion of people with learning disabilities or who face language barriers.

The contact form could also (or additionally) be protected by non-CAPTCHA methods such as:

* Checking POSTs to the form's action have been preceeded by GET requests for the form page.

* Tricking bots with dummy "Do not fill in this field" form fields that are labelled as such and also hidden with CSS.

* Limiting the frequency of POSTs from any given IP.

* Rejecting duplicate POSTs.

* Rejecting POSTs containing content that looks like spam or other abuse.

See also:

[http://www.arraystudio.com/as-workshop/the-captcha-alternatives.html](http://www.arraystudio.com/as-workshop/the-captcha-alternatives.html)

[http://webaim.org/blog/2007/03/07/spam_free_accessible_forms/](http://webaim.org/blog/2007/03/07/spam_free_accessible_forms/)

While such protection could be (relatively easily) cracked by writing a custom script, there would be no commercial incentive to do so, since a contact form is not bulk spam vector.

Although the contact form couldn't be used for spam, obviously users wishing to annoy the admins could use it. If the admins fear that the volume of verbal abuse sent via this form would still be too high to cope with, I am happy to set up a dedicated email account to which they could forward all form submissions. I would volunteer to sort out genuine requests and forward them on to forum administrators who could then add accounts for the users in question.

Making it clear that the person who reads the email doesn't work on any other aspect of the forum would also reduce the amount of abuse.

---

### Post by ubuntu-geek on 2007-09-10
We've discussed this in the past. I've added it to this months FC agenda ( starts in 30 mins) to start a more broader discussion. Some of the options you list are not feasible for us to implement.

---

### Post by ubuntu-geek on 2007-09-10
The forum council decided that we understand the current captcha is flawed however we need to keep it in place in order to prevent spam. We decided the unofficial alternatives available are not suitable and we hope there will be improvements to the official vbulletin captcha code in the near future.

---

### Post by benjaminhawkeslewis on 2007-09-11
If you could specify what was judged unsuitable about the solutions presented, others may be either able to fix flaws in those solutions, or suggest new, better ones. For example, if there's a problem with the reCAPTCHA plugin from the Forum Council's perspective, perhaps it can be fixed.

---

### Post by AlvinBarret on 2008-07-17
The forum [council]("http://www.councilors.co.uk") decided that we understand the current captcha is flawed however we need to keep it in place in order to prevent spam.:guitar   :

---

