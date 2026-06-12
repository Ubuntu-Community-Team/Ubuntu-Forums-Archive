---
title: "Installing NetBeans"
date: 2006-08-09
forum: Desktop Environments
---

### Post by ngdias on 2006-08-09
I downloaded and installed NetBeans from [http://www.netbeans.info](http://www.netbeans.info) (it was a .bin file with both NetBeans and the SDK)

I can open the program using the terminal, so I guess it's working ok.

The thing is I'd like to have it in the Applications menu, under Programming, but better yet would be to have it available under the Add/Remove software list. I tried looking for a package (I enabled universe) but I didn't find any.

Then I tried 'Add downloaded packages' in the Synaptic Package Manager but it doesn't seem to accept .bin files (they're greyed out).

Maybe if it's not too hard I could make a package from the .bin file?

---

### Post by loell on 2006-08-09
you can edit the menu, to reflect netbeans on programming section

---

### Post by ngdias on 2006-08-09
Thanks, but where do I edit the menu?

And what about the package question?

---

### Post by gordonyb0 on 2006-08-09
you can make a new link in /usr/share/applications/
the *.desktop files r the menu linking file u can make a new one such as NetBeans.desktop and write ur new lines with an editor.
That's it.:-P

---

### Post by loell on 2006-08-09
the reason why there is no specific debian package of netbeans might be,
because bin package is already sufficient. you can always uninstall netbeans by executing the uninstaller script in .netbeans directory.

---

### Post by ngdias on 2006-08-11
> **loell said:**
> the reason why there is no specific debian package of netbeans might be,
because bin package is already sufficient. you can always uninstall netbeans by executing the uninstaller script in .netbeans directory.

Ok, right, but a package would allow for automatic updates of the software, right?

And thanks for the help. Turns out that by just running Alacarte Menu Editor, it automatically adds a link for NetBeans in the menu. Neat. Very neat.

---

