---
title: "Kopete Spell Check Problem"
date: 2005-12-19
forum: Desktop Environments
---

### Post by Zotova on 2005-12-19
I've recently started using Kopete and I have noticed that the spell checker seems not to work. I had installed Kopete and tried it out when I was using Gnome. However since I've switched to KDE the spell check seems to no longer work.

I'm 90% sure it worked before in gnome although cannot be certain. I am also using KDE 3.5 - when in gnome I installed whatever version of kopete came with 3.4 then upgraded it to the version which comes with 3.5 when I installed KDE 3.5. (Hopefully that bit makes sense)

Other KDE programs use the spell checker and they work fine - for example the spell check in kmail, kword etc all work fine.

This is the error I get, in the screenshot below I typed a simple word 'test' into the chat window but switched the e and s around so it was highlighted as mis-spelled. I have also tried selecting different dictionaries - all produce the same error in kopete.

[img]http://www.shanghai.me.uk/kspell.jpg[/img]

Anyone know why the spell checker in kopete is getting errors like this and more importantly how to fix it?

Thanks in advance.

---

### Post by cwaldbieser on 2005-12-19
[QUOTE=Zotova]I've recently started using Kopete and I have noticed that the spell checker seems not to work. I had installed Kopete and tried it out when I was using Gnome. However since I've switched to KDE the spell check seems to no longer work.

I'm 90% sure it worked before in gnome although cannot be certain. I am also using KDE 3.5 - when in gnome I installed whatever version of kopete came with 3.4 then upgraded it to the version which comes with 3.5 when I installed KDE 3.5. (Hopefully that bit makes sense)

Other KDE programs use the spell checker and they work fine - for example the spell check in kmail, kword etc all work fine.

This is the error I get, in the screenshot below I typed a simple word 'test' into the chat window but switched the e and s around so it was highlighted as mis-spelled. I have also tried selecting different dictionaries - all produce the same error in kopete.

[img]http://www.shanghai.me.uk/kspell.jpg[/img]

Anyone know why the spell checker in kopete is getting errors like this and more importantly how to fix it?

Thanks in advance.[/QUOTE]

I am not sure if I am following this correctly.  Are you saying that what it is showing in the spellchecker window is not text you highlighted for it to spell check, but something else entirely different?

---

### Post by Zotova on 2005-12-19
Thanks for the reply.

Basically it doesn't matter if I highlight a word, or just spell check a few sentances. I always get what is in the screenshot - which looks to me like some html which is broken.

[edt] Also this might be worth mentioning. The autospell check never stays on, I have to select it each time I open a kopete chat window - where as in kmail for example once I'd turned it on it stayed on.

---

### Post by cwaldbieser on 2005-12-19
[QUOTE=Zotova]Thanks for the reply.

Basically it doesn't matter if I highlight a word, or just spell check a few sentances. I always get what is in the screenshot - which looks to me like some html which is broken.

[edt] Also this might be worth mentioning. The autospell check never stays on, I have to select it each time I open a kopete chat window - where as in kmail for example once I'd turned it on it stayed on.[/QUOTE]
That is a little strange-- if you click through the spelling replacements, does it show you any more of this weird HTML page?  Maybe a title tag that would give a hint as to where it is coming from?

Does switching from using Ispell to Aspell help at all?  

I don't have KDE 3.5, so the help I can offer is somewhat limited.  I have heard that sometimes when you upgrade KDE versions, settings left over in your ~/.kde directory can cause problems.  You might try renaming this folder temporarily to see if that helps.

I made some scripts over in the Customization section that will let KDE users spell check any text that is copied to the clipboard--  you might find it useful if you can't get the kopete auto-spell to work:
[http://www.ubuntuforums.org/showthread.php?t=102136]("http://www.ubuntuforums.org/showthread.php?t=102136")

---

### Post by Zotova on 2005-12-19
Thanks for the reply. I've being google-ing since I last posted and I read that aspell is generally better at suggesting words however is of no use if you don't use an English language. With being en-uk I switched to aspell but the problem was still there.

However I turned off rich text in a chat window - clicked spell check and everything worked fine. Close the window and reopen rich text gets re-enabled and the problem is back.

Also to answer your question, if I click ignore it will eventually make its way through the html and get to the word I actually want to check.

I've also tried reinstalling ispell and kopete - neither had any effect.

So two questions.

Does anyone know how to disable rich text permanently in kopete (I can't find a setting anywhere).

Or does anyone know how to get aspell/ispell whichever to spell check html and ignore the actual html content.

[edit]Just re-read your post:

> I don't have KDE 3.5, so the help I can offer is somewhat limited. I have heard that sometimes when you upgrade KDE versions, settings left over in your ~/.kde directory can cause problems. You might try renaming this folder temporarily to see if that helps.

I only used kopete in gnome a few times (didn't like it then). At that time I didn't have kde installed - I then added the kde 3.5 repo and installed all of kde. So I wouldn't have though it would be a left over directory - maybe something gnome did to kopete?

---

### Post by One Quick Question on 2005-12-20
The problem comes from the new version of Kopete.  It has issues, I'm afriad.
I don't know any fixes other than to wait for the next version (since it's already in their [bug](http://bugs.kde.org/show_bug.cgi?id=117600) tracker).

And unfortunately, disabling rich text (which is in Settings > Configure > Colors & Fonts > "Do not show user specified rich text") doesn't correct the problem :-\

EDIT:  I take that back, if you disable rich text on individual chat windows (by clicking the Disable rich text button which is on the Main Toolbar by default (I *think*, I've changed my buttons around)), then there are no HTML tags to spellcheck.
An annoying solution though.

---

