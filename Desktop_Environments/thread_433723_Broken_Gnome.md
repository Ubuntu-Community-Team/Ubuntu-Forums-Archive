---
title: "Broken Gnome"
date: 2007-05-05
forum: Desktop Environments
---

### Post by chedabob on 2007-05-05
I tried following the instructions for making Ubuntu look like Mac OS X, using the .debs from this post [http://ubuntuforums.org/showpost.php?p=2591836&postcount=532](http://ubuntuforums.org/showpost.php?p=2591836&postcount=532)

Now I have no panel at all. I just have a bar in the top left corner with the menu for GAIM. I also get a bunch of "I've detected a panel already open. Quitting" when I log in. I also have loads of dependencies missing:

```
The following packages have unmet dependencies.
  gnome-panel: Depends: libatk1.0-0 (>= 1.13.1) but 1.12.3-0ubuntu1 is installed
               Depends: libc6 (>= 2.5-0ubuntu1) but 2.4-1ubuntu12.3 is installed
               Depends: libcairo2 (>= 1.4.2) but 1.2.4-1ubuntu2 is installed
               Depends: libdbus-1-3 (>= 0.94) but 0.93-0ubuntu3.1 is installed
               Depends: libdbus-glib-1-2 (>= 0.73) but 0.71-1ubuntu1 is installed
               Depends: libebook1.2-9 (>= 1.10.1) but 1.8.1-0ubuntu5 is installed
               Depends: libecal1.2-7 (>= 1.10.1) but 1.8.1-0ubuntu5 is installed
               Depends: libedataserver1.2-9 (>= 1.10.1) but it is not installable
               Depends: libedataserverui1.2-8 (>= 1.10.1) but 1.8.1-0ubuntu5 is installed
               Depends: libfontconfig1 (>= 2.4.0) but 2.3.2-7ubuntu2 is installed
               Depends: libglib2.0-0 (>= 2.12.9) but 2.12.4-0ubuntu1 is installed
               Depends: libgnome-keyring0 (>= 0.7.1) but 0.6.0-0ubuntu2 is installed
               Depends: libgnomeui-0 (>= 2.17.1) but 2.16.1-0ubuntu2 is installed
               Depends: libgnomevfs2-0 (>= 1:2.17.90) but 2.16.1-0ubuntu7 is installed
               Depends: libpango1.0-0 (>= 1.16.2) but 1.14.5-0ubuntu1 is installed
               Depends: libxml2 (>= 2.6.27) but 2.6.26.dfsg-2ubuntu4 is installed
               Depends: libxrandr2 (>= 2:1.2.0) but 2:1.1.1-0ubuntu1 is installed
  gtk2-engines-pixbuf: Depends: libatk1.0-0 (>= 1.13.1) but 1.12.3-0ubuntu1 is installed
                       Depends: libc6 (>= 2.5-0ubuntu1) but 2.4-1ubuntu12.3 is installed
                       Depends: libcairo2 (>= 1.4.0) but 1.2.4-1ubuntu2 is installed
                       Depends: libglib2.0-0 (>= 2.12.9) but 2.12.4-0ubuntu1 is installed
                       Depends: libpango1.0-0 (>= 1.16.2) but 1.14.5-0ubuntu1 is installed
  gtk2.0-examples: Depends: libatk1.0-0 (>= 1.13.1) but 1.12.3-0ubuntu1 is installed
                   Depends: libc6 (>= 2.5-0ubuntu1) but 2.4-1ubuntu12.3 is installed
                   Depends: libcairo2 (>= 1.4.0) but 1.2.4-1ubuntu2 is installed
                   Depends: libfontconfig1 (>= 2.4.0) but 2.3.2-7ubuntu2 is installed
                   Depends: libglib2.0-0 (>= 2.12.9) but 2.12.4-0ubuntu1 is installed
                   Depends: libpango1.0-0 (>= 1.16.2) but 1.14.5-0ubuntu1 is installed
                   Depends: libpng12-0 (>= 1.2.13-4) but 1.2.8rel-5.1ubuntu0.1 is installed
                   Depends: libxrandr2 (>= 2:1.2.0) but 2:1.1.1-0ubuntu1 is installed
  libgtk2.0-0: Depends: libatk1.0-0 (>= 1.13.1) but 1.12.3-0ubuntu1 is installed
               Depends: libc6 (>= 2.5-0ubuntu1) but 2.4-1ubuntu12.3 is installed
               Depends: libcairo2 (>= 1.4.0) but 1.2.4-1ubuntu2 is installed
               Depends: libcupsys2 (>= 1.2.7) but 1.2.4-2ubuntu3 is installed
               Depends: libfontconfig1 (>= 2.4.0) but 2.3.2-7ubuntu2 is installed
               Depends: libglib2.0-0 (>= 2.12.9) but 2.12.4-0ubuntu1 is installed
               Depends: libpango1.0-0 (>= 1.16.2) but 1.14.5-0ubuntu1 is installed
               Depends: libpng12-0 (>= 1.2.13-4) but 1.2.8rel-5.1ubuntu0.1 is installed
               Depends: libxrandr2 (>= 2:1.2.0) but 2:1.1.1-0ubuntu1 is installed
  libgtk2.0-bin: Depends: libatk1.0-0 (>= 1.13.1) but 1.12.3-0ubuntu1 is installed
                 Depends: libc6 (>= 2.5-0ubuntu1) but 2.4-1ubuntu12.3 is installed
                 Depends: libcairo2 (>= 1.4.0) but 1.2.4-1ubuntu2 is installed
                 Depends: libfontconfig1 (>= 2.4.0) but 2.3.2-7ubuntu2 is installed
                 Depends: libglib2.0-0 (>= 2.12.9) but 2.12.4-0ubuntu1 is installed
                 Depends: libpango1.0-0 (>= 1.16.2) but 1.14.5-0ubuntu1 is installed
                 Depends: libpng12-0 (>= 1.2.13-4) but 1.2.8rel-5.1ubuntu0.1 is installed
                 Depends: libxrandr2 (>= 2:1.2.0) but 2:1.1.1-0ubuntu1 is installed
  libpanel-applet2-0: Depends: libatk1.0-0 (>= 1.13.1) but 1.12.3-0ubuntu1 is installed
                      Depends: libc6 (>= 2.5-0ubuntu1) but 2.4-1ubuntu12.3 is installed
                      Depends: libcairo2 (>= 1.4.2) but 1.2.4-1ubuntu2 is installed
                      Depends: libfontconfig1 (>= 2.4.0) but 2.3.2-7ubuntu2 is installed
                      Depends: libglib2.0-0 (>= 2.12.9) but 2.12.4-0ubuntu1 is installed
                      Depends: libgnome-keyring0 (>= 0.7.1) but 0.6.0-0ubuntu2 is installed
                      Depends: libgnomeui-0 (>= 2.17.1) but 2.16.1-0ubuntu2 is installed
                      Depends: libgnomevfs2-0 (>= 1:2.17.90) but 2.16.1-0ubuntu7 is installed
                      Depends: libpango1.0-0 (>= 1.16.2) but 1.14.5-0ubuntu1 is installed
                      Depends: libxml2 (>= 2.6.27) but 2.6.26.dfsg-2ubuntu4 is installed
                      Depends: libxrandr2 (>= 2:1.2.0) but 2:1.1.1-0ubuntu1 is installed
E: Unmet dependencies. Try using -f.

```

Any ideas?

Thanks

---

### Post by zvacet on 2007-05-05
Install dependencies and see what happend.Nothing bad,I belive.

---

### Post by chedabob on 2007-05-05
I used google to look for the .debs, but whenever the gdebi package manager runs, it tells me I have dependencies missing, and to run "sudo apt-get install -f", which is what yields the list above.

Any ideas?

---

### Post by ComplexNumber on 2007-05-05
are you running dapper, edgy, or feisty? i bet that you may have mixed a few up (eg even though you may be running (say) edgy, you've used some feisty  packages)....which will result in various unmet dependencies because they won't be in the repos.

---

