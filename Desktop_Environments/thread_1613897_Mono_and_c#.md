---
title: "Mono and c#"
date: 2010-11-05
forum: Desktop Environments
---

### Post by halen666 on 2010-11-05
Hi,
I am sorry for asking this stupid question, but why do people use c# to write applications when they can use java?. Likewise, why do I have to install mono in windows to run c# applications when I already have .net installed? I know mono is like an open source version of .net; however, I thought the purpose of mono was to write applications to make them portable, so that they can be run in windows and linux.  (like java). Then  why would I have to have it in windows to run application when I already have .net

Can I write applications on windows in c# and run them in linux just by using mono?. I am sorry for all these stupid questions. I am just confused.

---

### Post by GregBrannon on 2010-11-05
Recommend move to Programming Talk.

---

### Post by Seq on 2010-11-05
> **halen666 said:**
> Hi,
I am sorry for asking this stupid question, but why do people use c# to write applications when they can use java?.

Mostly developer preference. Why C over C++? Why Python over Perl? Why bash over zsh? etc.

> **halen666 said:**
> Likewise, why do I have to install mono in windows to run c# applications when I already have .net installed? I know mono is like an open source version of .net; however, I thought the purpose of mono was to write applications to make them portable, so that they can be run in windows and linux.  (like java). Then  why would I have to have it in windows to run application when I already have .net

I recall there being some slight variations in the compiled bytecode that mono produced that was required to be properly portable that had the side effect of being incompatible with microsoft's implementation. Aside from that, the biggest reason to require mono on windows is library support. Mono includes a bunch of libraries (gtk#, etc) that are not included in microsoft's .net implementation.

As for portability (run on windows and linux): It does that, but you need the Mono runtime. Just like you need to have Java installed to run java apps.

> **halen666 said:**
> Can I write applications on windows in c# and run them in linux just by using mono?. I am sorry for all these stupid questions. I am just confused.

No, mono can't run a compiled .net application, you would need to consider installing microsoft's .net implementation in WINE. However, if your code does not use any microsoft-specific libraries, you can probably take your code and easily compile it on Mono. MonoDevelop uses the same project files Visual Studio does, so this conversion should be pretty painless. You'll probably have to touch up your code in a few places, though.

---

### Post by directhex on 2010-11-05
> **halen666 said:**
> Hi,
I am sorry for asking this stupid question, but why do people use c# to write applications when they can use java?.

Because Mono is much MUCH lighter on resources than Java? Or because C# is a much more advanced language than Java? There are a couple of reasons.

>  Likewise, why do I have to install mono in windows to run c# applications when I already have .net installed?

You don't. But you may need some libraries found in Mono to run an app built for those libraries - e.g. Mono.Posix works on MS.NET, but where will you get it from?

> I know mono is like an open source version of .net; however, I thought the purpose of mono was to write applications to make them portable, so that they can be run in windows and linux.

Not the purpose, but usually a side-effect.

> (like java). Then  why would I have to have it in windows to run application when I already have .net

It's a good way to test the functionality and portability if you can minimise the differences from "os and runtime" to just "runtime" - that way bugs specific to the runtime and not the os are clearer.

> Can I write applications on windows in c# and run them in linux just by using mono?. I am sorry for all these stupid questions. I am just confused.

Yes, if you aren't using libs not found or available in Mono, or using p/invokes into Windows libs. I understand Pinta is developed on Windows, for example.

---

### Post by directhex on 2010-11-05
> **Seq said:**
> I recall there being some slight variations in the compiled bytecode that mono produced that was required to be properly portable that had the side effect of being incompatible with microsoft's implementation.

You recall wrong, the bytecode is defined in the ECMA documentation, which Mono follows. 

> No, mono can't run a compiled .net application, you would need to consider installing microsoft's .net implementation in WINE.

Also wrong. Apps compiled on MS.NET may not run on Mono due to the libs used or platform-specific code, but that's not always the case. You can definitely use assemblies compiled with csc on Mono.

---

### Post by Seq on 2010-11-05
> **directhex said:**
> You recall wrong, the bytecode is defined in the ECMA documentation, which Mono follows. 

I was running off memory. I thought I read something about a neccessary change in bytecode on Miguel's blog a few years ago. I can't seem to find any reference to that now, so I concede my point.

> **directhex said:**
> Also wrong. Apps compiled on MS.NET may not run on Mono due to the libs used or platform-specific code, but that's not always the case. You can definitely use assemblies compiled with csc on Mono.

I'll admit I was wrong. It appears to even be the [first item in the FAQ]("http://www.mono-project.com/FAQ:_General"). It is not completely clear to me from that wording, but I assume since the bytecode is standardized that this compat works both ways (assuming you're only using common libraries, have mono libs on windows, or are doing runtime detection and dynamic loading of equivalent platform specific libraries)?

---

### Post by directhex on 2010-11-05
> **Seq said:**
> I assume since the bytecode is standardized that this compat works both ways (assuming you're only using common libraries, have mono libs on windows, or are doing runtime detection and dynamic loading of equivalent platform specific libraries)?

Right.

---

