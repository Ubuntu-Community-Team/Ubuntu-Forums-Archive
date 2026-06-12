---
title: "[SOLVED] Programming in C# in Ubuntu?"
date: 2009-01-07
forum: General Help
---

### Post by vonsperb on 2009-01-07
I'm just wondering; What tools such as an IDE and runtime libraries could I use to write a few C# applications in Ubuntu? Thanks!

---

### Post by whoop on 2009-01-07
The default .NET framework is not developed to work with linux distros. If you want to run C# byte code on linux you should install mono. A descent IDE woudl be MonoDevelop: [http://www.monodevelop.com/Release_notes_for_MonoDevelop_0.12](http://www.monodevelop.com/Release_notes_for_MonoDevelop_0.12)

Hope this helps.

---

### Post by directhex on 2009-01-08
> **whoop said:**
> The default .NET framework is not developed to work with linux distros. If you want to run C# byte code on linux you should install mono. A descent IDE woudl be MonoDevelop: [http://www.monodevelop.com/Release_notes_for_MonoDevelop_0.12](http://www.monodevelop.com/Release_notes_for_MonoDevelop_0.12)

Hope this helps.

Install mono-devel on Jaunty, or mono-2.0-devel on older releases. "gmcs" is the C# compiler.

Install monodevelop for an IDE.

---

### Post by vonsperb on 2009-01-08
Thank you all!

---

