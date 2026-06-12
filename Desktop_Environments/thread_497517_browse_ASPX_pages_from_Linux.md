---
title: "browse ASPX pages from Linux?"
date: 2007-07-10
forum: Desktop Environments
---

### Post by bcw on 2007-07-10
Hello,

From ubuntu, I want to browse ASPX pages being served from a Windows machine.  Konqueror and Firefox don't.  IE running with WINE does partly, but that's not a solution.  I need to find a free software browser, so I can make a minimal browser for a custom app.

Is there anything?  Does installing mono allow the browsers to see ASPX?  I cannot host the ASPX on linux, so XSP isn't part of the solution.

Thanks for pointers.

Bret

---

### Post by Happy_Man on 2007-07-10
Have you tried Opera?

---

### Post by DoktorSeven on 2007-07-10
.aspx pages *served* on a Windows machine through IIS should not be a problem at all when viewed in any browser, since they in the end simply send HTML to a browser (see [Microsoft Help And Support](http://support.microsoft.com/default.aspx), for instance).  If you're trying to view .aspx any other way (file view, etc), this won't work since ASPX pages are meant to be served via a Web server like IIS. If IIS is misconfigured (it's not sending ASPX pages as text/html, for example), this might cause problems as well.

They can be served through Apache as well using Mono, though it might not be 100% compatible.  Do a search on Google for a howto.

---

