---
title: "Missing Firefox (1.0.7) Import Wizard"
date: 2005-12-30
forum: Desktop Environments
---

### Post by misGnomer on 2005-12-30
When I upgraded to Breezy and ran FF for the first time it ran the Import Wizard without asking and migrated my Mozilla data (bookmarks, settings, passwords etc.) over.

After logging in to family account I found FF to be there as expected but running it opened a vanilla profile and there is no File -> Import option in the menus.

Where's that 'Import Wizard' menu option? Can FF be started from the terminal with a parameter to run it?

Have people seen this behavior and what's the recommended fix? Creating a new profile (-p option) and manually moving the Mozilla files over?

---

### Post by misGnomer on 2005-12-30
The affected family account also had the "$home/.dmrc has incorrect permissions" (whatever that means) issue after Hoary -> Breezy upgrade if that's relevant, but the import option's still missing from the menus and the automatic Import Wizard never kicked in there...

---

### Post by misGnomer on 2005-12-30
According to Firefox documentation there's supposed to be "Import" menu option under "File".

Could someone kindly check if their Ubuntu-packaged FF has that "Import" option or if it's been intentionally omitted for some reason?

= = = =
[http://www.mozilla.org/support/firefox/menu#fileimport](http://www.mozilla.org/support/firefox/menu#fileimport)

"Import...
    Opens the Import Wizard, which allows you to import options, bookmarks, history, passwords and other data from browsers like Microsoft Internet Explorer, Netscape, Mozilla or Opera."
= = = =

Has everyone else already dumped this official 1.0.7 version for the non-Ubuntu v1.5?

---

### Post by dcstar on 2005-12-30
[QUOTE=misGnomer]When I upgraded to Breezy and ran FF for the first time it ran the Import Wizard without asking and migrated my Mozilla data (bookmarks, settings, passwords etc.) over.

After logging in to family account I found FF to be there as expected but running it opened a vanilla profile and there is no File -> Import option in the menus.

Where's that 'Import Wizard' menu option? Can FF be started from the terminal with a parameter to run it?

Have people seen this behavior and what's the recommended fix? Creating a new profile (-p option) and manually moving the Mozilla files over?[/QUOTE]
Importing Bookmarks is available from Bookmarks-Manage Bookmarks, the rest - I don't know.

---

### Post by misGnomer on 2005-12-30
Could you check if you have that "Import" menu option under "File"?

I've searched far and wide for a (comprehensive) Mozilla/Firefox startup parameter listing to find the one that invoked the "import wizard" for my own user profile but without luck.

---

### Post by dcstar on 2005-12-30
[QUOTE=misGnomer]Could you check if you have that "Import" menu option under "File"?

I've searched far and wide for a (comprehensive) Mozilla/Firefox startup parameter listing to find the one that invoked the "import wizard" for my own user profile but without luck.[/QUOTE]
No, and as far as I can tell that is no longer in FF.

It looks like you just copy the .mozilla directory from the old location to your new home directory.

---

### Post by hoodwink on 2005-12-30
[QUOTE=dcstar]No, and as far as I can tell that is no longer in FF.
[/QUOTE]
I'm not sure how much this helps. Isn't Firefox 1.0.7 an ancient version? I'm running 1.5 Beta2. The import option isd certainly live and well there, and I've used it.

---

### Post by misGnomer on 2005-12-30
The family (another user) home directory already has a fully customized ~/.mozilla/default/xxxxxxxx.slt directory and Moz1.7 uses it happily.

The problem is that Firefox 1.0.7 never offered to migrate the family account's Mozilla settings, and the Import Wizard which migrated my own account's Moz1.7 settings just fine during its first run is no longer available.

Hmm, I've occasionally ran the family account's Mozilla using "gksudo --user familyaccount 'mozilla -browser' under my own login account in order to easily add them bookmarks and to let them have a quick browsing session without needing to switch users. That has worked perfectly, but I recall trying to run Firefox using the same gksudo (as another user) trick during its  first run under that idnetity (it came up in its vanilla version without having imported the Moz settings).

Maybe I'll just delete the vanilla profile (~/.mozilla/firefox/xxxxxxx.default ;; "default"?) it created and try running Firefox again, this time actually logged in to the family account.

If everything goes haywire I can always dump the Ubuntu-packaged v1.0.7 and do an "unofficial" install of the Firefox 1.5. That should import the existing Mozilla profile properly.

PS. As I noted earlier and linked to the Mozilla documentation, there really should be a "File -> Import" option...  I you don't have it either, perhaps the Ubuntu packager chose to exorcise it from the xml/chrome of their version.

---

### Post by misGnomer on 2005-12-30
Somewhat offtopic as it turns out, but I finally found a list of Mozilla's command line parameters, but there is no option to start Mozilla (or firefox) with the Import Wizard. Perhaps the Wizard only runs automatically when there is no existing Firefox profile.

[http://www.mozilla.org/docs/command-line-args.html](http://www.mozilla.org/docs/command-line-args.html)

---

### Post by misGnomer on 2006-01-02
OK, turns out that simply renaming/deleting the default vanilla Firefox profile in the other user's home directory and then running firefox again while logged into that account gave Firefox a fresh start and the import wizard kicked in and migrated the Mozilla settings alright.

Now I can open the "family version" of Firefox using "gksudo --user familyaccount firefox", but for some reason I can only do that when my own instance of Firefox isn't already running.  :-( 

Running Mozilla that way can open a concurrent instance for another user.

Could someone with more than one account (and access, i.e. password, to both accounts) try if they can open a concurrent instance of *Firefox*. Either the Ubuntu-packaged 1.0.7, or the official 1.5?

E.g. Try if this works while already running Firefox as current user:

     gksudo --user <another-username> firefox

---

