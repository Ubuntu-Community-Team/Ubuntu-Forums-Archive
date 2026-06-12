---
title: "Emerald themes in Gutsy"
date: 2007-12-08
forum: Desktop Effects &amp; Customization
---

### Post by PaulFXH on 2007-12-08
Just got Gutsy running well after upgrading from Feisty (actually had to do a clean-install but that`s another story).
Compiz-fusion works fine too but something`s not quite right with my Emerald themes.
In Emerald Theme Manager, a total of 30 themes show up (OK, I know it`s not bad, but some of my favorite ones are missing).
I think the problem may be to do with those "infamous" Fetch buttons under the Repositories tab.
And, Yes, I have Subversion installed but when I click the Fetch GPL`d Themes a dialog comes up for about one second and goes away again. That doesn`t look promising.
The other button (non GPL`d Themes) stays alive for longer, maybe 5 seconds, but then stops when I get an error message saying "Error calling tar". This comes up 4 times in a row and then the dialog disappears.
Anybody know what`s happening here?

---

### Post by Matuku on 2007-12-29
*Bump*

I have the same issue, except that I have no Emerald themes beyond those that I have manually installed; none come with emerald and the Fetch GPL'd/non-GPL'd themes buttons bring up a downloading dialogue for about 2 seconds and it then vanishes and I have no new themes. I've checked Synaptic and it says that subversion is installed.

---

### Post by Forlong on 2007-12-29
The Emerald version in Gutsy points to an outdated source.

You have to either add themes manually (check [http://gnome-look.org](http://gnome-look.org) etc.) or you could just install the [package for feisty](http://packages.ubuntu.com/cgi-bin/download.pl?arch=all&file=pool%2Funiverse%2Fe%2Femerald-themes%2Femerald-themes_0.2.1-0ubuntu1_all.deb&md5sum=40b7e970de248d7b04e3aced4f4908fb&arch=all&type=main) (don't worry, it's safe in this case) but this contains only the GPL'd ones, of course.

---

