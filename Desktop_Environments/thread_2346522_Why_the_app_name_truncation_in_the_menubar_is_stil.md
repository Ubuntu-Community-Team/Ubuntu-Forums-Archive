---
title: "Why the app name truncation in the menubar is still there?"
date: 2016-12-15
forum: Desktop Environments
---

### Post by ardi2 on 2016-12-15
I feel quite puzzled about something that, IMHO, is perhaps the only bad style item in Unity, and which has been there for quite a few years: The truncation that happens in the app name at the menu bar. Yes, I like to have the menu bar always at the top. And I understand the need to display the app name, so that you know the app the menu belongs to. But, really, the reason I read for truncating it makes no sense to me: it's said that it is for avoiding the menu entries move when you maximize a window. Well, it's far better that the menu entries move than losing the app name. It's very distracting and annoying to see the app name not only truncated, but even too close to the menu entries, like almost getting mixed with it.

And the most puzzling of all is that this was filed as a bug, some mockups and solutions were discussed, and a fix was finally decided. The bug report now appears as "fixed". But, how exactly was it fixed? I see all app names that take more than a word merciless truncated. [Here is the bug report]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/619477") if you wish to take a look at it.

BTW, is there anyway of allocating more space to the app name so that more apps fit without truncation? Alternatively, can I hide the app name? (yes, I prefer to not see the app name rather than seeing it truncated).

---

### Post by vasa1 on 2016-12-15
I think the support aspect of the post is mainly in the last paragraph:> 
BTW, is there anyway of allocating more space to the app name so that more apps fit without truncation? Alternatively, can I hide the app name? (yes, I prefer to not see the app name rather than seeing it truncated).I don't understand the "allocating more space" part, but you may want to look at whether Compiz or some tweak tool allows you to hide the app name.

On the other hand, depending on your actual needs, you may want to explore a more flexible desktop environment. I get the impression that both GNOME and Unity prefer to have things a certain way. Environments such as KDE, XFCE, LXDE, and Mate offer the user more flexibility.

Re. the earlier part of the post, I couldn't find any description of the fix in the body of that page. But I'm guessing it involves adding an ellipsis after the first word (or after so many letters if the first word is "too long") and eliminating the rest.

---

### Post by mc4man on 2016-12-16
App names aren't truncated here in unity panel except when menu is shown which by default is only 1st. 3 sec after opening & then on mouse over.

---

### Post by ardi2 on 2016-12-17
> **vasa1 said:**
> I think the support aspect of the post is mainly in the last paragraph:I don't understand the "allocating more space" part, but you may want to look at whether Compiz or some tweak tool allows you to hide the app name.

On the other hand, depending on your actual needs, you may want to explore a more flexible desktop environment. I get the impression that both GNOME and Unity prefer to have things a certain way. Environments such as KDE, XFCE, LXDE, and Mate offer the user more flexibility.

Re. the earlier part of the post, I couldn't find any description of the fix in the body of that page. But I'm guessing it involves adding an ellipsis after the first word (or after so many letters if the first word is "too long") and eliminating the rest.

I consider Unity the best desktop I've found. I come from the Mac and it is the desktop that best resembles my workflow on the Mac (yes, it even beats ElementaryOS if I want to mimic my Mac workflow).

But the app name truncation is really distracting to me. I don't understand why it's kept in that way, it seems to be accepted as the desired behavior rather than a bug, and it really makes look Unity as it was broken. I don't understand it, given how easy it would be to fix it (a perhaps not perfect but reasonably good and obvious solution would be to allocate space for app names with two or three words, because the nonsense is that even the standard Unity apps -such as Software Center- get their name truncated)

---

### Post by howefield on 2016-12-17
So what version of Ubuntu are you using and perhaps a screenshot showing your issue might be helpful ?

Something feels wrong with your particular installation rather than being an universal issue.

---

### Post by ardi2 on 2016-12-19
> **howefield said:**
> So what version of Ubuntu are you using and perhaps a screenshot showing your issue might be helpful ?

Something feels wrong with your particular installation rather than being an universal issue.
It's on 16.04 LTS. And it is an universal issue, AFAIK. For example, look at the ugly truncation of the GIMP app name at the menu bar in [this screenshot I found]("http://i1-news.softpedia-static.com/images/news2/ubuntu-16-04-lts-to-let-users-change-the-visibility-of-app-menus-in-unity-panel-500305-3.jpg") just googling typing *unity menu 16.04* as keywords. It should be "GIMP Image Editor", but it gets truncated to "GIMP Im" which melts into the "File" menu entry. As I said, given how Ubuntu takes care of aesthetics, I really don't understand why this is left as supposedly correct behavior (because the app name truncation has always been there as far as I can remember, from the first Unity release until today).

Anyway, can this be fixed with any workaround? Any way for allocating more space for the app name in the menubar, so that only exaggeratedly long apps get truncated?

---

### Post by vasa1 on 2016-12-19
You were asked to provide a screenshot in post #5. That may help others understand your point. You may need to take a "delayed" screenshot. Check the **man** pages of your screenshot tool for how to do so.

---

### Post by ardi2 on 2016-12-19
> **vasa1 said:**
> You were asked to provide a screenshot in post #5. That may help others understand your point. You may need to take a "delayed" screenshot. Check the **man** pages of your screenshot tool for how to do so.
I did include an screenshot in my last post. Ok, it's not an screenshot from my machine, but one I found googling, because I'm not seated at my box in this moment. I can provide an screenshot from my box if it's necessary, but however I feel that posting another one I found by googling shows the issue is universal, and not specific to my installation.

---

### Post by howefield on 2016-12-19
> **ardi2 said:**
> It's on 16.04 LTS. And it is an universal issue, AFAIK.

Obviously, it must be universal with the only respondents to your thread unable to reproduce and no one else corroborating the "issue"!! That isn't to say it is not an issue with your set up but it most certainly can't be described as universal.

>  For example, look at the ugly truncation of the GIMP app name at the menu bar in [this screenshot I found]("http://i1-news.softpedia-static.com/images/news2/ubuntu-16-04-lts-to-let-users-change-the-visibility-of-app-menus-in-unity-panel-500305-3.jpg")

What ?

Are you talking specifically only about when the menus are shown

---

### Post by ardi2 on 2016-12-19
> **howefield said:**
> Obviously, it must be universal with the only respondents to your thread unable to reproduce and no one else corroborating the "issue"!! That isn't to say it is not an issue with your set up but it most certainly can't be described as universal.



What ?

Are you talking specifically only about when the menus are shown
Of course. I was talking about the app menu bar, so the issue can only be seen when the menu is shown. If you turn menus permanent in the Appearance settings, it's obviously more annoying because you see the truncated names constantly. If you keep the default of just showing the menu when hovering, you only see the glitch when you hover the mouse over the menu. But, no matter how frequently you see it, it's a distracting glitch, not only because the name is truncated, but because it's so close to the menu bar that it looks like if something was broken.

EDIT: At the very least, I'd expect that none of the Ubuntu default bundled apps had their names truncated. It's weird that even them get trimmed.

---

### Post by mc4man on 2016-12-19
This behavior came from a longstanding bug from global menu detractors who wanted menus back in the window. Eventually some fixes arose as LIM (Locally-Integrated-Menus). Additions to that allowed the LIM option to include menus in windows as always shown or on hover.
So that option was really intended for LIM though it has affect when using global menus which have always been in the current spot & the fact that on hover (the current & historical default) having them 'truncate' a window name was no big deal & intentional.

I guess one could file a bug on that particular combo if not already but seeing as though unity7 is & has been in maintenance mode since prior to 14.04 not extremely likely it would be addressed. I would term that option as 'provided but not supported'.

---

