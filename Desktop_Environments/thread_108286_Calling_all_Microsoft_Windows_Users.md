---
title: "Calling all Microsoft Windows Users"
date: 2005-12-25
forum: Desktop Environments
---

### Post by nami on 2005-12-25
Hi

Can someone please confirm this for me.  Please check this through both microsoft windows and ubuntu linux.  I have noticed that the ubuntu has blurry font unlike microsoft windows.  Please have a look at the screenshots below and carefully look at the font in the paragraph "Ubuntu is a complete Linux-based operating system, freely available with both community and professional support. It is developed by a large community and we invite you to participate too!"

On my ubuntu system it's blurry but on both my microsoft windows systems its super sharp.  If this is the case with all ubuntu systems, when looking at the microsoft windows screenshots through ubuntu will also appear blurry, so please have a lot at them again using microsoft windows.

I have taken various screenshots using different browsers.  2 from microsoft windows 2000 using internet explorer and firefox, 1 from microsoft windows xp using internet explorer, and 1 from ubuntu 5.10 using firefox.  All screenshots are sharp except ubuntu

microsoft windows 2000 ie
[[IMG]http://img349.imageshack.us/img349/5762/windows2000ie9id.th.png[/IMG]](http://img349.imageshack.us/img349/5762/windows2000ie9id.png)

microsoft windows 2000 ff
[[IMG]http://img484.imageshack.us/img484/5769/windows2000ff7ot.th.png[/IMG]](http://img484.imageshack.us/img484/5769/windows2000ff7ot.png)

microsoft windows xp ie
[[IMG]http://img325.imageshack.us/img325/6215/windowsxpie3kf.th.png[/IMG]](http://img325.imageshack.us/img325/6215/windowsxpie3kf.png)

ubuntu 5.10 ff
[[IMG]http://img502.imageshack.us/img502/5624/ubuntu510ff7lk.th.png[/IMG]](http://img502.imageshack.us/img502/5624/ubuntu510ff7lk.png)

I have noticed that all applications in ubuntu have slightly blurry text, it's almost like ubuntu has antialiasing enabled on all fonts by default or something.  If this is true, how do you turn it?

All the above screenshots are 24bit lossless png files!

Thanks for reading.

nami

---

### Post by 23meg on 2005-12-25
Try disabling hinting in System / Preferences / Font / Details .

---

### Post by aysiu on 2005-12-25
Why don't you go to System > Preferences > Fonts and set it up how you want? Anti-Aliasing as far as I know is a *good* thing, and it's not enabled by default in Ubuntu (or in Windows).

---

### Post by pharcyde on 2005-12-25
After looking through those screen shots I can't tell the difference at all.  I guess my eyes just aren't as sensitive as yours are.   But like the other posts suggest just modify your system settings to display the fonts you prefer best.

---

### Post by kaamos on 2005-12-25
And in windows (I think xp and newer only) you can turn antialising on by selecting "smooth edges of screen fonts" somewhere in display preferences. Or whatever that damn box was called.. ;)

---

### Post by sciurus on 2005-12-25
I think you have antialiasing turned on in Ubuntu but not in Windows. To me, the Windows fonts look terrible; far too jagged. However, if that's the appearance you like, set font rendering to "monochrome" in System-Preferences-Fonts.

---

### Post by nami on 2005-12-25
Unfortunately, that is the font appearance I like! :) 

Here are the images 800% zoomed.

Nice and crisp in windows
[IMG]http://img426.imageshack.us/img426/125/windows8008zq.png[/IMG]

Not so crisp in ubuntu
[IMG]http://img452.imageshack.us/img452/9321/ubuntu8009gz.png[/IMG]

I've tried changing the settings in the font screen, but can't seems to get it to look like windows.

Oh well!

Thanks anyway.

nami

---

### Post by 23meg on 2005-12-25
Did you disable subpixel smoothing too? Take a look at [this]("http://www.ubuntuforums.org/showthread.php?t=20976").

---

### Post by briancurtin on 2005-12-25
maybe its just me, but in the regular non-ridiculously zoomed in pictures, the fonts in ubuntu/firefox look much better than any of the windows combinations.

in particular, look at W and Y letters in both. its my preference, but they look way better than the jagged cuts of the windows fonts

---

### Post by 23meg on 2005-12-25
Freetype2 which is the font rendering engine in use in Ubuntu and Cleartype have different ways of smoothing fonts, so the same font can look slightly different at the same size and on the same display in the two systems. This is more true for certain sizes than others, and Freetype2 seems to render certain fonts better than others, due to the way they're hinted. It's best to experiment with different fonts and sizes, try both the autohinter module and native hinting, and stick with what you find the most usable. My main font is Bitstream Vera Sans 10px at a display resolution of 72 DPI set in both Font preferences and xorg.conf (see the thread I linked to in my last post for info on setting it up in xorg.conf) and I find it more pleasing to look at and easier on the eyes on my LCD display than Verdana 10px rendered by Cleartype, which was my former favorite.

[[IMG]http://img358.imageshack.us/img358/7360/bsvs7dn.png[/IMG]](http://imageshack.us)

---

### Post by anil_robo on 2005-12-25
How to make fonts look crisp:

1. Go to System-->Preferences-->Font
2. Change the following:
Application font: Bitstream vera Sans Roman
Desktop font: Bitstream vera sans roman
Window title font: Bitstream vera sans bold
Leave the terminal font to whatever it is.
3. In font rendering, select Subpixel smoothing if you're using a laptop. Try other combinations as well. I have subpixel smoothing always, but I've seen many people opting for Best shapes and Best contrast as well.

Ubuntu rocks!

---

### Post by nami on 2005-12-26
> ...and that people should have the freedom to customise and alter their software in whatever way they see fit.

That quote can be found on the front page of [www.ubuntu.com](www.ubuntu.com).

I understand and appreciate the fact that some people like the blurry effect, so you have no need to customise that.  However, I don't like the blurry effect, so I feel the need to customise it in a way that I see fit.

Anyway, thanks for the links, I'll try going through them and hopefully, it will help sharpen up the fonts! :)

Thanks for all the help.

nami

---

### Post by nami on 2005-12-26
Hi

The instructions in that link worked perfectly! :)

After restart: Everything much sharper.
[[IMG]http://img321.imageshack.us/img321/3498/screenshot5sm.th.png[/IMG]](http://img321.imageshack.us/img321/3498/screenshot5sm.png)

Before restart: Browser text much sharper.
[[IMG]http://img357.imageshack.us/img357/1551/screenshot7xd.th.png[/IMG]](http://img357.imageshack.us/img357/1551/screenshot7xd.png)

Original: Too blurry for my liking.
[[IMG]http://img502.imageshack.us/img502/5624/ubuntu510ff7lk.th.png[/IMG]](http://img502.imageshack.us/img502/5624/ubuntu510ff7lk.png)

Thanks for helping me fix this!

nami

---

