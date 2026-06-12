---
title: "Openbox and Xinerama"
date: 2005-04-17
forum: Desktop Environments
---

### Post by smoon on 2005-04-17
I switched from Debian Sid to Ubuntu two days ago. All went fine so far except that Openbox behaves really odd. For example if I maximize a window, it gets stretched over my two screens, windows get placed inbetween my two screens and so forth.

I'm using the same configuration here as I did with Sid and a few other distributions before. This is the first time I encountered such a behaviour. Is the Ubuntu Openbox package using some special patches? Or am I missing something?

---

### Post by nad on 2005-04-17
Were you using the xorg x server? I suspect that you need to tweak some config files.

Dan M

---

### Post by smoon on 2005-04-17
Yeah, I was using Hoarys Xorg packages with Sid as well, I even used exactly the same xorg.conf.

The odd thing is, there seems to be no difference between the Hoary and the Sid Openbox package, so it must be something else. But I can't imagine what this is since I'm using the same X Server, the same graphics card drivers, the same configuration files, ...

Anyone has an idea what could cause the different behaviour?

---

### Post by nad on 2005-04-17
Any differences between the Xorg packages you used? Take a look at your gdm logs and configs maybe.

Dan M

---

### Post by smoon on 2005-04-18
No, no differences in the Xorg packages - at least none that I am aware of. As I stated before: I used Hoarys Xorg packages with Sid. The logs don't tell me anything than the usual warnings (Missing fontpaths, xrdb overriding this or that *background value, ...).

I'm going to try out what Openbox does if I set NVidias NoTwinViewXineramaInfo to true...


*Edit*
Changed nothing. But I came across this one:
> On Sun, 2005-04-17 at 12:27 +0200, Mark Gjøl wrote:
> Juris Bune wrote:
> > Hello!
> > 
> > There is one annoying problem with openbox in Twin View X-server
> > mode(desktop is extended to my TV). Other window managers(kwin,
> > metacity) seem to behave the "right" way when maximizing application
> > windows e.g. windows are maximized to physical display(only one),
> > depending on which display the window is located. But openbox treats
> > both physical displays as one and maximizes window across whole "virtual
> > desktop".
> > 
> > I believe this is not the way it should me. Although it might not
> > qualify as a bug rather it is more like a wish for future releases.
> > 
> > BTW, could this be that I am the only one who noticed this? :) Seems so
> > if we trust in google.com.
> 
> Works fine for me... Debian/Sid openbox 3.2.

Well, Mark, you are right! Just made a "dirty" install of Debian Sid
openbox package and everything was fine. Damn, seems it is Ubuntu
package maintainers fault.

Thanks for feedback!

From the [Openbox Mailinglist](http://icculus.org/cgi-bin/ezmlm/ezmlm-cgi?24:mss:3454:200504:mlhclgdgamghdfejcmjn)

---

### Post by nad on 2005-04-18
Hoary has had dozens of Xorg versions. Reading through the Xorg changelog is like reading War and Peace. Yes, if both installs were uptodate there shouldn't be any differences.

I am not familiar with the Openbox package. I am interested in Xorgs' capabilities as I run multicard/multihead/multiconsole setups and it has been a real challenge over the past several months.

I don't have similar problems with the XFree86 X server.

Dan M

Edit: Good catch on the broken openbox package.

---

### Post by trash-can on 2005-04-18
I had the same problem with openbox in TwinViem mode. I took openbox executable from Sid package and everything is fine. I gues it something with Ubuntu openbox package.

---

### Post by smoon on 2005-04-18
Ok, it's definately the Ubuntu Openbox package that's causing this behaviour. I just installed the Openbox deb from Sid and it works like a charm... I'll investigate further on this to find out what's the problem with Ubuntus ob deb.

Thanks for your help Dan.

---

