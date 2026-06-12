---
title: "Getting Rid of the Fonts Problems"
date: 2009-01-12
forum: General Help
---

### Post by Prosis on 2009-01-12
Hello

I would like to get rid, once and for all, of the font problems I have.  Under Gnome, fonts are easily customizable and that's not my problem.  The problem arrives on the Web.  

Many websites I have made have a horrible rendering on Ubuntu (or any Linux distro for that matter) even though I have msttcorefonts installed as well as TrueType fonts from Windows and that my Ubuntu Firefox is configured the same way as my Windows Firefox, etc.

For example, statdemtl.qc.ca on Ubuntu uses Arial Narrow which is taller than the real font used on the website.  That causes the text in the side boxes to overstep the actual box.  Same thing for matthewgood.org which Ubuntu Firefox applies Arial Narrow instead of the real font.

There's also the line height which is a lot bigger on Ubuntu Firefox than on Windows/Mac OSX.

Ubuntu gives me the worst rendering for web fonts.  That's the only thing that stops me from using only Ubuntu on my PC given that I'm a web programmer. I don't want to have to use ubuntu except when I work when I'd have to use a virtual machine.  A VM to test is OK but not to work.

Can someone help me?

I have tried a lot of things I found on the net but nothing has worked.

Thank You

---

### Post by jimv on 2009-01-12
Maybe I'm not noticing something, but they look fine to me.  How do you tell what font Firefox is using?

Also, do the pages look the same if you use Opera?

---

### Post by Prosis on 2009-01-12
Well it was just a guess from the looks of it.  If you go to the box called " A TICKET TO PAY?" on statdemtl.qc.ca, does the text overstep the box?

I haven't used Opera, I could try it to see if the problem is Firefox.

---

### Post by jimv on 2009-01-12
I see the E sticking out; I didn't notice that before.

I just turned off "hinting" in the advanced font settings (details button), now it looks the same as on my Windows box.

EDIT

Setting hinting to "Slight" makes it appear ok too.

---

### Post by Prosis on 2009-01-12
Do you use a .fonts.conf?

If so, can I have it lol ;)

---

### Post by Prosis on 2009-01-12
No it doesn't work.  Here's what it looks like on mine

---

### Post by mssever on 2009-01-12
> **Prosis said:**
> No it doesn't work.  Here's what it looks like on mine
I see the same thing as your screenshot. What's wrong with it? It looks fine to me.

---

### Post by Prosis on 2009-01-12
The "To Find Out More" section should be inside the square.

---

### Post by mssever on 2009-01-12
Without looking at the website's source, I'm going to guess that it's a bug in the website. It's simply not possible to assume that fonts will render on screen in an identical fashion across multiple systems. There are simply too many variables. It'd be interesting to find out how this looks on a Mac. Web designers who assume that fonts will look the same on their users' systems as they do on their own are in for an unpleasant surprise. All this is to say that I don't think there's a problem on the Linux side, *per se*. I think the problem is with the web developer who didn't adequately test the site.

---

### Post by Prosis on 2009-01-12
> **mssever said:**
> Without looking at the website's source, I'm going to guess that it's a bug in the website. It's simply not possible to assume that fonts will render on screen in an identical fashion across multiple systems. There are simply too many variables. It'd be interesting to find out how this looks on a Mac. Web designers who assume that fonts will look the same on their users' systems as they do on their own are in for an unpleasant surprise. All this is to say that I don't think there's a problem on the Linux side, *per se*. I think the problem is with the web developer who didn't adequately test the site.

No no I made the website.  And it was tested on both Windows (IE6, IE7, Firefox, Safari and Chrome) and on Mac OSX (Firefox and Safari).

---

### Post by mssever on 2009-01-12
> **Prosis said:**
> No no I made the website.  And it was tested on both Windows (IE6, IE7, Firefox, Safari and Chrome) and on Mac OSX (Firefox and Safari).
Well, it appears that Linux uses different font rendering techniques. Not surprising, really. And since you made the site, re-configuring your system won't address the other Linux users who visit your site. Basically, your choices are: a) live with it; or b) change your site in such a way that things look right in all OSes.

---

### Post by Prosis on 2009-01-12
> **mssever said:**
> Well, it appears that Linux uses different font rendering techniques. Not surprising, really. And since you made the site, re-configuring your system won't address the other Linux users who visit your site. Basically, your choices are: a) live with it; or b) change your site in such a way that things look right in all OSes.

But as stated in my original message, it's the same thing for other websites.  And if jimv says it works for him, then there must be a way.

---

### Post by mssever on 2009-01-12
> **Prosis said:**
> But as stated in my original message, it's the same thing for other websites.  And if jimv says it works for him, then there must be a way.
I might be missing the point, but I'm looking at this from the perspective of a web developer. Websites can't depend on users to reconfigure their machines. Websites just have to deal with whatever they're given. If you reconfigure your system, then you won't be able to adequately test your own site.

---

### Post by Prosis on 2009-01-12
I see what you mean.  But what I would like is for Ubuntu to render websites like OSx and Windows does.  If not I can always change my way of making websites but the others won't.  And since I've managed to change the way Firefox shows a website (not enough yet) I'm hoping that there's a way to get it to my linking.

---

