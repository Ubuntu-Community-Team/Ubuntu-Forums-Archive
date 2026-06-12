---
title: "Support Forums Help"
date: 2007-03-26
forum: Forum Feedback &amp; Help
---

### Post by AlanRogers on 2007-03-26
This is not a rant or a criticism of any of those people who give of their freely time and knowledge to these fora but I have noticed what is (to me) a disturbing trend in the offer of support and would appreciate some discussion around so that I can decide (for myself thanks) whether I'm being a paranoid whinging git or it's a real issue.

The challenge is simple; developers and supporters both appear to lean heavily towards the latest and greatest version of anything, seeming to forget that not all of us are using it or even prepared to.

For example, I've been using a great tool which I've managed to install from outside of the repositories. On its own dedicated forum, I've received rapid and informative answers to questions raised but the challenge is that the solution is to install the latest version, which is in the repositories.

All of this is true but in a limited way; it's in the Feisty repositories and Feisty is still in Beta! I use Dapper which is LTS and therefore supported for another 2+ years so this latest version of the application isn't therefore available to me without a steep learning curve.

I've asked if it can be backported but that's perhaps not a question for the developer. Can developers and supporters please bear in mind that not all of us are using/willing to use/capable of using the latest greatest Beta release?

---

### Post by mips on 2007-03-26
You could always build your own.

---

### Post by AlanRogers on 2007-03-26
I realise that's an option but it's a tad above my current position on my climb up the steep learning curve. I also suspect that it's potentially beyond others new to Ubuntu Linux and/or converting from a Windows mindset.

If I may be so bold, that was a very rapid and short response to my question which comes across as dismissive. Was that the intent? It that's the case, what's the purpose of an LTS version, if developers just ignore it in favour of the newest version?

---

### Post by PriceChild on 2007-03-26
I'm not quite sure what you want...

Dapper is an LTS and is rock solid and stable. It is rock solid and stable because it is frozen. You can't just go round upgrading all the packages constantly as that would affect the stability.

Developers and Maintainers spend ample time on Dapper, ensuring it is constantly patched with critical bug fixes and security updates.

If you want the latest apps... then use them?

---

### Post by AlanRogers on 2007-03-26
> **PriceChild said:**
> I'm not quite sure what you want...If you want the latest apps... then use them?Then my point was probably lost in my verbosity. To reiterate, is it reasonable to say that a program is available in the repositories when the only repositories that it's available in are those for the unstable beta release? Is this misleading to users who are not, and refuse to be, on the bleeding edge?

I can't install the latest version of the software in question because I can't trouble-shoot the unresolved dependancies in the DEB file but that's an issue that I'll raise in the appropriate forum. The version which is touted for Dapper is downloadable off the developers site, but as a tarball, which entails learning on my part to install it, because it isn't a DEB or in the repositories.

I can overcome these learning issues, if I can be bothered to spend the necessary time and effort, after which I will know more. The question is was the original advice correct/appropriate/justifiable/misleading?

Is my point clearer or have I just clouded it further?

---

### Post by PriceChild on 2007-03-26
If I understand you correctly... absolutely no version of the package that you want is availiable in Dapper?

If that's correct well then I'm afraid "tough". The backports project helps fix some of these problems, but I'm not sure they would pull back completely new packages, especially with annoying dependencies. Still worth asking though maybe... [http://ubuntuforums.org/forumdisplay.php?f=41](http://ubuntuforums.org/forumdisplay.php?f=41)

The software won't be in the repo in the first place because no-one packaged it. To help avoid problems like this in future, if you want software in the repository then do something about it yourself: [https://wiki.ubuntu.com/MOTU/Packages/New](https://wiki.ubuntu.com/MOTU/Packages/New) :)

---

### Post by AlanRogers on 2007-03-26
PriceChild, thanks for the clarity. I can't actually check that from here because I'm at work on Windows. :( However, I will check this evening. ISTR that there was a repository hosted outside of Ubuntu, but that's defunct I think.

I'm not sure that I'm ready for doing packages of my own yet but at least I know the process and purpose of backports. I appreciate the candour and apologise for the confusion. Back to normality ...

---

