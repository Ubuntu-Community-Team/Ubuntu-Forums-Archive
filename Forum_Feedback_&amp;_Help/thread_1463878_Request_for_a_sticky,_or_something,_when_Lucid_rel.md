---
title: "Request for a sticky, or something, when Lucid releases"
date: 2010-04-27
forum: Forum Feedback &amp; Help
---

### Post by Mr. Picklesworth on 2010-04-27
There is a lot of misinformation bouncing around about changing window button order in Ubuntu Lucid. Whenever someone asks about moving buttons back to the left, someone seems to pop in telling them to do it with gconf-editor by changing the /apps/metacity/general/button_layout key. That works, but it isn't the right approach and it perpetuates the myth that window button order is hard to configure, that this change is evil, etcetera.

So, new in Lucid is the ability for a meta-theme (the big icons in the Theme section of *Appearance Preferences*) to individually specify a window button layout. Currently Dust, Impression, Radiance and Ambience use this to provide unusual button orders. The default, however, is still the older order (menu on left; minimize, maximize and close on right). So, if you definitely aren't happy with buttons being on the left, simply choose a different theme. (Homosapien is a really cool one!)

If you still want the Ambience or Radiance theme but with buttons on the right, choose one of those other themes, press the Customize button, and have fun!

This change makes it easier for themes to do interesting things with window borders :)

Unfortunately, if the wrong approach spreads, they won't be able to do that.

---

### Post by Elfy on 2010-04-27
We are talking about that now amongst the staff. There will be at some point a sticky.

---

### Post by alvevind on 2010-04-28
What I finally did was:
1. System > Preferences > Appearance
2. Select the theme icon "New Wave"
3. Click the button "Customize.."
4. Select tab "Controls" and select value "Ambiance"
5. Select tab "Window border" and select value "Ambiance"
6. Select tab "Icons" and scroll down and select value "Ubuntu-mono-dark"
7. Close. Close.
8. HAPPY!!!

NOTE:

In my first confused attempt at following Mr Prickesworths instructions I only got to customize the window buttons, and was not too happy with the halfway result. Only afterwards did I realize I could customize the Controls too and that that would yield the desired results.

Please, when offering the best-practice solution spell out **every single step** the user must take as verbose as possible. Do **not** assume the user has any intelligence whatsoever. 
Remember "Linux for human beings"!

---

### Post by coffeecat on 2010-04-28
> **forestpiskie said:**
> There will be at some point a sticky.

Thanks for that, but I hope it will be soon. It's not just in this forum that misinformation is bouncing around. It seems that half the internet is telling people to use gconf-editor. Out of interest I googled "move window buttons to right in mac os" (No, I don't want to. I was curious to know if it could be done.) and a lot of the hits were about moving the window buttons in Ubuntu. With gconf-editor.

:frown:

---

### Post by cariboo on 2010-04-28
That's probably because the subject has been covered so often and in so many different sub-forums.

---

### Post by sisco311 on 2010-04-28
never mind :)

---

### Post by mc4man on 2010-04-28
May be missing something here - while it's simple to do in appearances it does initially seem  counter-intuitive

The meta theme icons (which appear to control button placement) should reflect the actual placement of that theme - some on right, some on left instead of all on right.

The customize - window border icons shouldn't show any buttons at all or should change based on meta theme previously chosen or in effect.

---

### Post by Mr. Picklesworth on 2010-04-28
> **mc4man said:**
> May be missing something here - while it's simple to do in appearances it does initially seem  counter-intuitive

The meta theme icons (which appear to control button placement) should reflect the actual placement of that theme - some on right, some on left instead of all on right.

The customize - window border icons shouldn't show any buttons at all or should change based on meta theme previously chosen or in effect.

It should, but that wasn't done on time. At any rate, I'm not saying my explanation of things should be stickied somewhere, and this thread isn't in the right section of the forum to be a support thread. I'm just saying that peoples' desire to have window buttons back on the right could drive some serious disinformation if it isn't approached in a solid, unified fashion :)

The directions I posted aren't the easiest, though, so here's a really simple direction:
Just open *Appearance Preferences*, click "Install..." and install this file:
[http://people.ubuntu.com/~dylanmccall/downloads/themes/Ambience_Radiance-Right.tar.gz](http://people.ubuntu.com/~dylanmccall/downloads/themes/Ambience_Radiance-Right.tar.gz)

(Nice and tiny, has both themes, explicitly sets the button layout).

Edit: Thanks for pointing out that problem, Alvevind. I just fixed it.

---

### Post by alvevind on 2010-04-28
(Comment removed. The theme Ambiant-right did not restore the ordering only the location so it might not be optimal solution. Prefer the customize solution in first post.) 

EDIT: 
Now the button ordering is corrected.
So last post from Mr.Picklesworth offers a very easy solution.

---

### Post by cariboo on 2010-04-28
This isn't a support thread, please keep on topic., which is a request for a sticky upon Lucid's release.

Suggestions for sticky additions are OK.

---

### Post by Digikid on 2010-04-29
Oh here is a CRAZY idea.

How about LISTENING to your fanbase for once and not changing things that the fanbase CLEARLY told you that they did not like and change it back.

Crazy Idea....I know.

---

### Post by djchandler on 2010-04-29
> **Mr. Picklesworth said:**
> There is a lot of misinformation bouncing around about changing window button order in Ubuntu Lucid. Whenever someone asks about moving buttons back to the left, someone seems to pop in telling them to do it with gconf-editor by changing the /apps/metacity/general/button_layout key. That works, but it isn't the right approach and it perpetuates the myth that window button order is hard to configure, that this change is evil, etcetera.

So, new in Lucid is the ability for a meta-theme (the big icons in the Theme section of *Appearance Preferences*) to individually specify a window button layout. Currently Dust, Impression, Radiance and Ambience use this to provide unusual button orders. The default, however, is still the older order (menu on left; minimize, maximize and close on right). So, if you definitely aren't happy with buttons being on the left, simply choose a different theme. (Homosapien is a really cool one!)

If you still want the Ambience or Radiance theme but with buttons on the right, choose one of those other themes, press the Customize button, and have fun!

This change makes it easier for themes to do interesting things with window borders :)

Unfortunately, if the wrong approach spreads, they won't be able to do that.

Yeah, I'm one of those guys advocating using gconf-editor. I don't follow why you say that's wrong. If it works, why is it wrong? Besides, what if an end-user doesn't want the "interesting things" going on in the borders that you are talking about? Surely there will be a gconf key to deal with those "interesting things" too. Gconf-editor is just another way to do something. I like desktop icons for my Trash, Home, Network and Computer too. I don't believe there's an easier way than using gconf-editor to get those back (as they appear in Debian, Fedora, etc.).](*,)

I do understand using a method that's easier and doesn't feel like you are editing a Windows registry key. The problem is, any way that would be intuitive other than switching themes then customizing would probably break with the upstream distribution at this time. You would probably have to add a new tab to the Appearances>Themes>Customize dialog. That would definitely be anathema.

What seems to be advocated here as the "proper" method is counter-intuitive at best. Yes it works, but how is it any easier? It's certainly a matter of opinion. And speaking of that, we also have some advocating running a script in the terminal window to do the same job. I do understand that needs to be nipped in the bud.

Agreed we need to all be on the same page here as more people find they would like the buttons on the right as Lucid adoption increases. A sticky is the very best way to do that. It will also serve to avoid multiple help requests getting asked in multiple forums about how to make the switch. Obviously we don't want what is actually a feature that allows customization of the desktop to become a source of FUD.

Isn't it wild how such a simple change has caused so much debate and controversy? But the cat is out of the bag now!
;-)

---

### Post by Mr. Picklesworth on 2010-04-29
> **djchandler said:**
> Yeah, I'm one of those guys advocating using gconf-editor. I don't follow why you say that's wrong. If it works, why is it wrong? Besides, what if an end-user doesn't want the "interesting things" going on in the borders that you are talking about? Surely there will be a gconf key to deal with those "interesting things" too. Gconf-editor is just another way to do something.

I do understand the reluctance, and indeed this is (for now) a patch applied downstream but most definitely making its way upstream.

For an example of why I am adamant my way is the one we should advocate, change your theme to something else, then change it back to Ambiance. There goes your customization, and there enters a confused user ;)

---

### Post by djchandler on 2010-04-29
> **Mr. Picklesworth said:**
> I do understand the reluctance, and indeed this is (for now) a patch applied downstream but most definitely making its way upstream.

For an example of why I am adamant my way is the one we should advocate, change your theme to something else, then change it back to Ambiance. There goes your customization, and there enters a confused user ;)

I'm with you on this. And you are right about the user becoming confused. And there could result an exit of the confused user. We all agree we don't want that.

So a sticky authored by you seems to be very much in order. My only other suggestion is that it needs to be placed prominently, perhaps in multiple forums besides **absolute beginners talk** and **general help**, throughout Ubuntu Forums.

BTW, check this thread.

[http://ubuntuforums.org/showthread.php?t=1465822](http://ubuntuforums.org/showthread.php?t=1465822)

---

### Post by Merk42 on 2010-04-30
> **Digikid said:**
> Oh here is a CRAZY idea.

How about LISTENING to your fanbase for once and not changing things that the fanbase CLEARLY told you that they did not like and change it back.

Crazy Idea....I know.

Oh here is a CRAZY idea.

How about the admins of this forum have NO CONTROL over any aspect of the Ubuntu interface, so they have to make the BEST of the situation and provide a sticky.

Crazy Idea....I know.

---

