---
title: "why the attraction of .net"
date: 2009-01-17
forum: Education &amp; Science
---

### Post by kapi on 2009-01-17
Hi,

just a general off the cuff question relating to the seemingly endless line of employers advertising for developers with asp.net or c#.net experience.

I studied web development at uni but only really touched on the asp.net in one module, I know css and XHTML, some XML etc and the basics in VB,Java.  So my question is, are employers just just jumping on the .net band wagon just because everyone else seems to be and as I've just moved to Ubuntu from vista which really ticked me off, what alternatives are there to .net in Linux. Because I must say Ubuntu has really impressed me.

Cheers

Kapi

---

### Post by meatpan on 2009-01-17
Selecting a programming platform is a complicated endeavor.  For better or worse, employers might choose .net because:

o The local talent pool is primarily experienced with .net.
o The company has been using microsoft products such as asp and vb, and the .net expansion was a logical upgrade, whereas a migration to competitors was seen as too much of a risk to quality and uptime.  (ie, the benefits of .net competitors did not outweight the cost of switching).
o The company doesn't know any better; the key decision maker was not aware of or experienced with alternatives to the microsoft stack.
o The company believes there's more money/contracts/opptys available for using .net in their market segment.  Perhaps their customers are locked in to microsoft products.

These are the typical reasons I have encountered, and their are undoubtedly more. Once again, these decisions might be for better or worse.

---

### Post by kapi on 2009-01-18
thanks for the insight

kapi

---

### Post by LaserJock on 2009-01-18
You'll want to have a look at [http://www.mono-project.com/](http://www.mono-project.com/)

---

### Post by directhex on 2009-01-19
Perhaps because there are some genuinely nice points to it? Seems odd, but it's true.

.NET was born from frustration. Back in the day, Microsoft realised that their primary programming platforms (e.g. VB6) were a mess, inviting insecurity and problems. They decided to focus their efforts on Java, but found that there were inadequacies with it (e.g. poor support for interop with existing C-based libraries; poor support for native look & feel on Windows) so they made their own modified version of Java with some "improvements" to these points (which sacrificed cross-platform, a point that at best MS didn't care about).

And Sun sued them over it.

So rather than give up completely, they designed their own "better" Java from scratch - like Java, but without the restriction of being built around one language (i.e. easy for many languages to interop with each other). Like Java, but without the 100 meg cross-dependent class library. Like Java, but actually standardized so anyone can make their own implementation easily. Like Java, but with easy interop with native libraries. Like Java, but with (sigh) better Windows-native behaviour.

Those are the primary advantages at a framework level. There are downsides too, of course, but people who blindly call .NET crap compared to Java are anti-MS people incapable of admitting reality to themselves.

For Linux, we have Mono, a Free Software .NET implementation designed to bring all the above advantages to Free Software app development, and stop people from needing to fight with C to write their apps (F-Spot and Tomboy in a default Ubuntu install are .NET apps written on Linux in C# which use Mono)

---

