---
title: "How to fix the &quot;Could not fetch ***blah***/Sources.gz or Releases.gz in Feisty!"
date: 2008-12-13
forum: General Help
---

### Post by jbitkill on 2008-12-13
Hi, this tut. is to show you how to update Feisty to the Gutsy repos!

Pre: Make sure no package/update manager is running!!! Backup the sources.list file!!!

1. In terminal, type in: (CHANGE GEDIT WITH YOUR FAVOURITE TEXT EDITOR!)
```

sudo gedit /etc/apt/sources.list
```

2. Then, go to Search > Replace or press Ctrl+H.

3. Enter in "Feisty" in the "Search for" box.

4. Enter in "Gutsy" in the "Replace with" box.

5. Click "Replace".

6. Go to File > Save or press Ctrl+S.

7. Close the text editor.

8. Go to your update/package manager and Reload or Check for updates.

Post: It now should come up with GUTSY versions of software, now upgrade while Gutsy still working!

---

