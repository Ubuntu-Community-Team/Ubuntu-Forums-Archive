---
title: "Ragnarok"
date: 2007-07-15
forum: Gaming &amp; Leisure
---

### Post by ghsx on 2007-07-15
Using wine, after login i get an error: Failed to connect

Using cedega, after login i get an error: Disconnected from server

anyone can help to solve this problem??

thx

---

### Post by cogadh on 2007-07-15
You have to manually apply patches. See Wine's AppDB page for details:
[http://appdb.winehq.org/appview.php?iVersionId=928](http://appdb.winehq.org/appview.php?iVersionId=928)

---

### Post by ghsx on 2007-07-15
i dont have problem with patches. i play in a private server (qro).

---

### Post by cogadh on 2007-07-15
Sorry about that, I saw the post on that page describing a failure to connect to patch server and thought that was the issue you were having. Did you add the DLL files and switch Windows emulation to Win 98 which seems to be required (also according to the posts on that page)?

---

### Post by ghsx on 2007-07-16
i added Mfc42.dll and i switched emulation to win98 but i still have the problem.

thx

---

### Post by orangebase on 2007-08-10
For Wine, this may be insightful: [http://bugs.winehq.org/show_bug.cgi?id=3962#c10](http://bugs.winehq.org/show_bug.cgi?id=3962#c10). You have to redirect traffic (or edit the server data in the .grf or something else).

---

