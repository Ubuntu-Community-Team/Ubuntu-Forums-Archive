---
title: "Is the forum Cookie dependent ?"
date: 2009-08-19
forum: Forum Feedback &amp; Help
---

### Post by Regenweald on 2009-08-19
I am using Chromium build 4.0.203.0 (23670). If i disable cookies in the browser I am constantly being logged out.

---

### Post by jpeddicord on 2009-08-19
> **Regenweald said:**
> I am using Chromium build 4.0.203.0 (23670). If i disable cookies in the browser I am constantly being logged out.

Yes. You must have cookies enabled do anything other than browse the forums. If you are concerned about privacy, try Chromium's Incognito mode.

---

### Post by Tamlynmac on 2009-08-21
jacobmp92

I find that response odd, unless it only applies to Chromium. I been on the forum for a while now and have never activated cookies in Firefox. Are you certain that cookies are required to participate?

I just checked my cookies and "Accept" is turned off in Firefox.

---

### Post by jpeddicord on 2009-08-21
I just tried it again, and it does seem that you are able to keep a session without cookies enabled. However, this only works if you never click any outside links to threads, and only click links from forum pages. The reason is that the session ID is stored in the URL to identify you. If you open a link that does not have that ID in it, the page won't have you marked as signed in.

It results in a severely crippled browsing experience. You will be signed out fairly often, whether it was because you entered from an external location or your session ID expires (I believe bapoumba mentioned the timeout was set to 30 minutes).

---

### Post by Regenweald on 2009-08-22
> **jacobmp92 said:**
> I just tried it again, and it does seem that you are able to keep a session without cookies enabled. However, this only works if you never click any outside links to threads, and only click links from forum pages. The reason is that the session ID is stored in the URL to identify you. If you open a link that does not have that ID in it, the page won't have you marked as signed in.

It results in a severely crippled browsing experience. You will be signed out fairly often, whether it was because you entered from an external location or your session ID expires (I believe bapoumba mentioned the timeout was set to 30 minutes).

Thanks jacobmp92, i think that this is exactly what was happening to me. since then i have been using the 'restrict third party cookies' option in Chromium as the sign out occurrence was quite random to begin with. this explains it.

---

