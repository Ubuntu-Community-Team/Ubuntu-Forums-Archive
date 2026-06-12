---
title: "What is AppleDouble? (and how do I get rid of it)"
date: 2009-03-18
forum: General Help
---

### Post by sdide on 2009-03-18
Hey.

I've recieved a file (._picture.eps) on an email as an attachment from a guy apparently using a Mac.

First off the beginning of the file "._" made me think something is not right.

I save the file, and the usual programs all fail to open it (evince, gimp, gs, et cetera) returning various error messages. 

$ file ._picture.eps
._picture.eps: AppleDouble encoded Macintosh file

Ok... so from macutil:

$ macunpack ._picture.eps
Premature EOF
$

So is the file corrupt or what is going on here?
Is there a better tool than macutil for AppleDouble encoding?

/Søren

---

### Post by mikewhatever on 2009-03-19
In my opinion, you should have just deleted the email with the attached file and never tried opening it.

---

### Post by mb_webguy on 2009-03-19
Take a look at [this]("http://en.wikipedia.org/wiki/AppleSingle").

From the description, it sounds like he sent you the second half of a dual-forked file.  An AppleDouble file is actually two files that combined do one thing.  For example, a document would have its text and formatting information in one file, and have any embedded images or similar information in the other.  The second such file begins with "._" to make it hidden.  I don't think you can open one without the other.

If you trust the guy who sent you the file, let him know he didn't send the whole thing.  Better yet, tell him to send you the info in a format you can use.

Otherwise, I'd delete it.  Dual-forked files aren't picky about what they can contain.  It's entirely possible that it could contain code.  While this shouldn't be a problem as long as you don't make the file executable and then execute it, there's no sense in trying your luck.

---

