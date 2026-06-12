---
title: "How Ubuntu makes tear-free desktop?"
date: 2012-09-23
forum: Desktop Environments
---

### Post by Noah_Danwell on 2012-09-23
Hello. I've worked with Ubuntu 12.04 and Ubuntu 10.04 and was admired that there is not any [tearing]("http://en.wikipedia.org/wiki/Screen_tearing") even "from scratch" with default video drivers.

I very apprectiate Ubuntu developers for this because i hate tearing.

But now i need to configure one Debian Stable (squeeze) desktop (based on Gnome too), and it has tearing.

Tell me, **which settings in Ubuntu ****are responsible **for tear-free desktop. I want to configure Debian's Gnome to achieve it on opensource drivers like it's done in Ubuntu.

My videocard is ATI HD 4850.

---

### Post by cmcanulty on 2012-09-23
what is tearing?

---

### Post by vexorian on 2012-09-23
He linked to the wikipedia page that explains what is tearing.

All I can say about this is, are you sure that Ubuntu's default video drivers used in your machine are open source ones? To me, latest ubuntu silently installs nvidia's drivers. But I am not so sure about ATI. Another thing could be that the driver versions in your ubuntu and debian are different.  And of course, are you comparing same desktop environments?

---

### Post by MG&amp;TL on 2012-09-23
> **Noah_Danwell said:**
> Hello. I've worked with Ubuntu 12.04 and Ubuntu 10.04 and was admired that there is not any [tearing]("http://en.wikipedia.org/wiki/Screen_tearing") even "from scratch" with default video drivers.

I very apprectiate Ubuntu developers for this because i hate tearing.

But now i need to configure one Debian Stable (squeeze) desktop (based on Gnome too), and it has tearing.

Tell me, **which settings in Ubuntu ****are responsible **for tear-free desktop. I want to configure Debian's Gnome to achieve it on opensource drivers like it's done in Ubuntu.

My videocard is ATI HD 4850.

I think, although I'm not sure, that Ubuntu tears too, but it's hidden behind compiz's 'blur' or 'fade' window plugin. I think Debian uses metacity by default.

Unless I'm mistaken, in which case vexorian's answer is probably a good option.

> **cmcanulty said:**
> what is tearing?

The trailing effect you get behind windows and applications where the WM doesn't draw fast enough.

---

### Post by mcduck on 2012-09-23
Compiz (the window manager used in Unity) has vertical sync enabled by default. So as long as it has detected your screen's refresh rate correctly that will take care of any tearing issues.

(and tearing is when the data sent to your display changes while the display is in the middle of the process of refreshing what's visible on the screen. If something on the screen is moving at the same time, you can get a visible seam in the image where bottom part of the display is showing where that moving object was on previous frame, and top part is already showing where it's located on the next frame. Vertical sync synchronizes updating the screen contents to the display's refresh rate so what's visible on the screen doesn't change while the display is drawing a frame.)

---

### Post by hansolo4949 on 2012-09-23
> **mcduck said:**
> Compiz (the window manager used in Unity) has vertical sync enabled by default. So as long as it has detected your screen's refresh rate correctly that will take care of any tearing issues.

(and tearing is when the data sent to your display changes while the display is in the middle of the process of refreshing what's visible on the screen. If something on the screen is moving at the same time, you can get a visible seam in the image where bottom part of the display is showing where that moving object was on previous frame, and top part is already showing where it's located on the next frame. Vertical sync synchronizes updating the screen contents to the display's refresh rate so what's visible on the screen doesn't change while the display is drawing a frame.)

Exactly. Tearing is created by either Vsync being disabled, or out of sync with your monitor's refresh rate, which if I had to guess, windows does NOT have enabled (hence your suprise).

---

### Post by Noah_Danwell on 2012-09-23
> **vexorian said:**
> All I can say about this is, are you sure that Ubuntu's default video drivers used in your machine are open source ones?
I'm not sure. But i'm ready to install any drivers to solve the tearing issue.

> **vexorian said:**
> Another thing could be that the driver versions  in your ubuntu and debian are different.
I think i can add any additional repos with fresh drivers.

> **vexorian said:**
> And of course, are you  comparing same desktop environments?
Gnome in Ubuntu 10.04 and Gnome in Debian Squeeze (both created in 2010 +/-).

> **MG&TL said:**
> I think, although I'm not sure, that Ubuntu tears too, but it's hidden behind compiz's 'blur' or 'fade' window plugin. I think Debian uses metacity by default.
So be it. The main thing that the tearing isn't seen.

> **mcduck said:**
> Compiz (the window manager used in Unity) has vertical sync enabled by default. So as long as it has detected your screen's refresh rate correctly that will take care of any tearing issues.
So, I need only install &#1057;ompiz? A specific version, or any?

---

### Post by mcduck on 2012-09-25
> **Noah_Danwell said:**
> 
So, I need only install &#1057;ompiz? A specific version, or any?
Yeah, using Compiz should fix that for you. And every version (perhaps apart from the very first ones from years and years ago) have had the settings for refresh rate and vsync.

---

