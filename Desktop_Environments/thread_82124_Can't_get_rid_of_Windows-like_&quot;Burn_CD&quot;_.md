---
title: "Can't get rid of Windows-like &quot;Burn CD&quot; dialog box..."
date: 2005-10-25
forum: Desktop Environments
---

### Post by irusun on 2005-10-25
Every time i put a blank CD or DVD into my DVD burner, I get the "Burn audio, photo or data CD?" dialog box.

Every time, I check the "Always take this action" box and then press cancel, i.e. I never want to see that dialog box ever again as long as I live, ever, ever, ever.  But the very next time I put a blank disc in the drive, I get the same message.  The only other options are Burn Audio CD, Burn Photo CD or Burn Data CD.

I don't want any "help" from gnome figuring out what I want to do with the disc... I already know what I want to do with the disc, and it doesn't involve that dialog box.

Does anyone know how to permanently turn that dialog box off?

I am reasonably handy with the configuration editor, but didn't see anything obvious.

Thanks!

---

### Post by heimo on 2005-10-25
This is educated guess. Change
/desktop/gnome/volume_manager/prompts/burn_cd
->burn_cd -> 8


If I change this to 0, the dialog will pop up and ask what I want to do with blank DVD, if I change it back to 8, dialog is gone and burn data cd option assumed.
[LIST]
[*]8 -> data
[*]6 -> audio
[*]7 -> photo[/LIST]

---

### Post by bionnaki on 2005-10-26
system>preferences>removable drives and media
uncheck "blank cd & dvd"

---

### Post by heimo on 2005-10-26
[quote=bionnaki]system>preferences>removable drives and media
uncheck "blank cd & dvd"[/quote] 
Yeah, it wasn't clear to me from the irusuns message if the wanted behaviour was to not ask question (popup dialog) and do nothing or not ask question and use the default behaviour. Unchecking the option as suggested should (to my understanding) disable the "help" from Gnome when inserting blank discs. Good point!

EDIT: Maybe I shouldn't be using English before three cups of coffee.

---

### Post by irusun on 2005-10-28
Thank you both for your responses.

[QUOTE=heimo]This is educated guess. Change
/desktop/gnome/volume_manager/prompts/burn_cd
->burn_cd -> 8[/QUOTE]

This was a pretty good try, but instead of getting the original dialog box, a new nautilus window opened up in its place... which was just as bad.

[QUOTE=bionnaki]system>preferences>removable drives and media
uncheck "blank cd & dvd"[/QUOTE]

This fixed it - this was what I was looking for.  Thank you, thank you, thank you!

I was getting ready to unleash a hissy fit of truely embarrassing proportions.  I can't tell you how disconcerting this whole Windows XP on the Linux desktop is for me... I've been a dedicated Linux user for several years now, but if Linux is going to end up a clone of Windows XP, I may as well go back to using Windows XP - it would be a lot less trouble...

---

### Post by Buffalo Soldier on 2005-10-28
Would it be better to change the **Cancel** button with **Do not popup** button? So that if we *check* **Always take this action**, next time the window won't automatically popup.

---

### Post by irusun on 2005-10-28
[QUOTE=Buffalo Soldier]Would it be better to change the **Cancel** button with **Do not popup** button? So that if we *check* **Always take this action**, next time the window won't automatically popup.[/QUOTE]
Well, you need to keep the cancel button for those who want to continue to see the dialog box but don't necessary need it at certain times... but yes, they should definitely add a "Do not ask me this again" button.

It would be really great if they would centralize the controls for all these pop-ups so as soon as I setup a user, I could turn them all off at once.

What's so disappointing (on top of the earlier "disconcerting"!) about all this is that it lacks any creativity or even common sense by the developers.  They seem so intent on copying an idea that's already proved to be a disaster... so much so that Microsoft itself is heading in a different direction.  Then the developers will try to catch up to whatever Microsoft is doing three years from now.  They'll always be trying to catch up to what Microsoft's doing.  They should stop this losing game of catch-up, and re-start by coming up with a *better* solution than what Microsoft is already doing.

---

