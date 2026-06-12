---
title: "Skype on the Ubuntu Forums?"
date: 2012-03-21
forum: Forum Feedback &amp; Help
---

### Post by dagroves on 2012-03-21
I see on peoples posts that there are buttons for the messengers they have. Skype is one of them. When I click on it, it brings up a pop up where I can view profile or message them, then it says that "Firefox don't know how to open this address because the protocol "skype" isn't associated with any program". What do I do to make this work?

---

### Post by dagroves on 2012-03-22
***bump***

---

### Post by CharlesA on 2012-03-22
Works for me. It just opens a window with different options to contact someone via Skype.

You do need Skype installed, of course.

---

### Post by dagroves on 2012-03-22
> **CharlesA said:**
> Works for me. It just opens a window with different options to contact someone via Skype.

You do need Skype installed, of course.


I do I have Skype installed, when I click on someone Skype it brings up the window with the different options to contact someone but then when I click on something it tells me that Firefox does not know how to open the Protocol "Skype".

---

### Post by CharlesA on 2012-03-22
Could be that Skype isn't set up with firefox. I don't use it so I don't know.

---

### Post by dagroves on 2012-03-22
> **CharlesA said:**
> Could be that Skype isn't set up with firefox. I don't use it so I don't know.
I think that is it but I have no idea how to do that!

---

### Post by oldos2er on 2012-03-22
I don't use Skype either, but Firefox's application settings are in Edit, Preferences, Applications.

---

### Post by cariboo on 2012-03-23
I don't have Skype installed on this system, but when I click on your (op's) skype icon I get a window popping up, see the screenshot. BTW I'm using chromium-browser here.

---

### Post by dagroves on 2012-03-23
The first screenshot is what happens when I click on my Skype thing on my posts or anyones.

The second one is what happens when I click on "View Profile" or any option.

The third one is when I click on "Already Have"

It's not something that is important, it is just bugging me!
What do I do?

---

### Post by kostkon on 2012-03-23
You could try the following solution:
> [LIST][*]Type about:config into the Location Bar (address bar) and press Enter.
    [*]Right-click -> New -> Boolean -> Name: network.protocol-handler.expose.skype -> Value -> false
    [*]Next time you click a link of protocol-type "skype" you will be asked which application to open it with.[/LIST]

Source [here]("http://community.skype.com/t5/Windows/Firefox-is-not-associated-with-any-progam-issues/td-p/421611").

Hope that helps.

---

### Post by dagroves on 2012-03-24
> **kostkon said:**
> You could try the following solution:


Source [here]("http://community.skype.com/t5/Windows/Firefox-is-not-associated-with-any-progam-issues/td-p/421611").

Hope that helps.

I just did that and it does not work.

---

