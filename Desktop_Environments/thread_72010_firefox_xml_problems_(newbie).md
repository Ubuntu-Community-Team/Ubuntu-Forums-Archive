---
title: "firefox xml problems (newbie)"
date: 2005-10-05
forum: Desktop Environments
---

### Post by bluflame_ignite on 2005-10-05
as a warning i am totally new to linux. i'm trying it out to see if i'd like to switch from windows to linux. so forgive any extreme stupidity and please try to talk in non-linux-technical terms.

whenever i download something in firefox (and sometimes when i just click links and things) , i get some kind of an error pop-up that says this:

    xml parsing error: not well-formed
    location: chrome://mozapps/content/downloads/unknownContentType.xul
    line number 1, column 2:
    k(aSavedToDisk)
    _^

or

    xml parsing error: not well-formed
    location: chrome://mozapps/content/downloads/downloads.xul
    line number 1, column 2:
    .Value, "FileExtensions") + ")";
    ^

or

    xml parsing error: not well-formed
    location: chrome://global/context/commonDialog.xul
    Line number 1, column 2
    ing);
    ^
in cases where the link is a direct link to the downloadable file, i can right-click and "save link as" and it will download, but the error still comes up. and cases where there's a scripted link to a download, i can't even get the file.

what am i doing wrong?

---

### Post by Mr Frosti on 2005-10-05
What extensions, if any, do you have installed for Firefox? It looks like the profile is damaged in some way for the user. Since this only happens when you download a file, what is the default action you have selected to perform? You can view this information by clicking Edit -> Preferences, and then looking at Downloads. The action associated with the file type you are trying to download can be edited.

If the issue is with your profile, try removing it and creating a new profile. For information on profile actions, look at this site:

[http://www.mozilla.org/support/firefox/profile]("http://www.mozilla.org/support/firefox/profile")

---

