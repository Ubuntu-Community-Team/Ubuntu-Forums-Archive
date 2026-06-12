---
title: "Unfortunate misinformation in malicious commands announcement"
date: 2008-03-23
forum: Forum Feedback &amp; Help
---

### Post by cevans on 2008-03-23
I can certainly understand the reason for the site-wide malicious commands announcement. However, I believe that it is vital that the information in that post be as accurate as possible; considering how widely-referenced it is, with so many people pointing to it in their signatures, and its very strong wording, I worry that innocent posters will be accused of maliciousness if there are errors in it, and users will eventually come to ignore it if those errors are not corrected.

My particular concern is with the claims it makes about 'rm -r .*'. While it claims that this is a malicious command, as .* will pick up .. and thus remove everything in higher directories, *no POSIX-compliant rm will ever do anything to . or ..* (even "rm a/." won't remove a). Per the POSIX Programmer's Manual:

> If either of the files dot or dot-dot are  specified  as  the  basename portion of an operand (that is, the final pathname component), rm shall write a diagnostic message to standard error and do nothing  more with such operands.

In fact, rm -r .* is a very useful command that I use frequently to remove hidden directories; it actually does what one would expect.

Unfortunately, I don't know who can correct this problem - I've PM'ed jdong, but have yet to receive any response.

---

### Post by LaRoza on 2008-03-24
> **cevans said:**
> 
My particular concern is with the claims it makes about 'rm -r .*'. While it claims that this is a malicious command, as .* will pick up .. and thus remove everything in higher directories, *no POSIX-compliant rm will ever do anything to . or ..* (even "rm a/." won't remove a). Per the POSIX Programmer's Manual:

In fact, rm -r .* is a very useful command that I use frequently to remove hidden directories; it actually does what one would expect.

Unfortunately, I don't know who can correct this problem - I've PM'ed jdong, but have yet to receive any response.

The admins will look at it. The announcment was written because of a sudden surge of malicious commands, and may have been slightly rushed.

---

