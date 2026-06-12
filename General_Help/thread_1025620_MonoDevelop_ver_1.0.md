---
title: "MonoDevelop ver 1.0 ?"
date: 2008-12-30
forum: General Help
---

### Post by BeShrewd on 2008-12-30
I used synaptic to install MonoDevelop, and it installed ver 1.0

According to the mono site there's a 2.1 version and the 1.91 version is what should go to ubuntu, when I try to get the package again it just tells me it's already installed.

I'm a complete newb and I have no idea what it is I did wrong here.

What I need is for System.Windows.Forms to work on C# and the older version of mono doesn't support it apparently.

How do I get the newer version?

---

### Post by directhex on 2008-12-30
> **BeShrewd said:**
> I used synaptic to install MonoDevelop, and it installed ver 1.0

According to the mono site there's a 2.1 version and the 1.91 version is what should go to ubuntu, when I try to get the package again it just tells me it's already installed.

You're confusing Mono (the framework) with MonoDevelop (the IDE)

Intrepid includes Mono 1.9.1, and MonoDevelop 1.0

> What I need is for System.Windows.Forms to work on C# and the older version of mono doesn't support it apparently.

libmono-winforms2.0-cil package for .NET 2.0+
libmono-winforms1.0-cil package for .NET 1.x

---

### Post by BeShrewd on 2008-12-31
So the mono version is right. I have both those libraries. Still no go.

To make sure it's not me that's doing something wrong I downloaded a couple samples of winforms code, and now I'm getting that *Windows, Drawing* both don't exist...

I'm really clueless as to what it may be.

---

### Post by directhex on 2008-12-31
> **BeShrewd said:**
> So the mono version is right. I have both those libraries. Still no go.

To make sure it's not me that's doing something wrong I downloaded a couple samples of winforms code, and now I'm getting that *Windows, Drawing* both don't exist...

I'm really clueless as to what it may be.

Perhaps you could paste the actual error

---

### Post by BeShrewd on 2009-01-01
```
The type or namespace name `Windows' does not exist in the namespace `System'. Are you missing an assembly reference?(CS0234)
```
```
The type or namespace name `Drawing' does not exist in the namespace `System'. Are you missing an assembly reference?(CS0234)
```

here it is, and the code would be
```
using System;
using System.Drawing;
using System.Windows.Forms;
```

---

### Post by directhex on 2009-01-01
> **BeShrewd said:**
> ```
The type or namespace name `Windows' does not exist in the namespace `System'. Are you missing an assembly reference?(CS0234)
```
```
The type or namespace name `Drawing' does not exist in the namespace `System'. Are you missing an assembly reference?(CS0234)
```

here it is, and the code would be
```
using System;
using System.Drawing;
using System.Windows.Forms;
```

And you're including appropriate assembly references? In MonoDevelop, go to the project pane, right-click on References, then Edit References - and ensure you tick next to System.Drawing and System.Windows.Forms

---

