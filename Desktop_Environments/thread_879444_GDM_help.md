---
title: "GDM help"
date: 2008-08-04
forum: Desktop Environments
---

### Post by Riffer on 2008-08-04
I'm trying to personalize my login screen with back ground pictures and such with not much luck.  I'm using GDMsetup and under the local tab selecting the pics I want.  The pics never come up though.  Any ideas?

---

### Post by Riffer on 2008-08-04
bump

---

### Post by Vadi on 2008-08-04
I think you need to create your own theme and install it. Don't know how to go about making one though

---

### Post by mcduck on 2008-08-05
You can't simply use pictures, you need proper themes.

And if you are actually trying to use themes now, make sure you select the theme you weant by activating it's radio button, simply clicking on the theme itself is not enough.

---

### Post by fuzzyk.k on 2008-08-05
well you could download a theme, extract it and then edit  it

---

### Post by Riffer on 2008-08-05
Know any good GDM theme editors?

---

### Post by kirsis on 2008-08-05
> **Riffer said:**
> Know any good GDM theme editors?

There aren't any theme-editor tools per se. Install a theme, browse to the folder (/usr/share/gdm/themes for system wide themes, I think) and modify it to your likening.

To test the theme out, while working on it, run:

```

gdmflexiserver --xnest

```

(you need to install xnest for this to work. sudo aptitude install xnest)

When you're satisfied, bundle it as a new theme (just an archive)

---

### Post by pauper on 2008-08-05
> Know any good GDM theme editors?

You can edit *.xml file with just about any editor. Same applies to *.desktop
files as well--copy path and append in CLI.

---

