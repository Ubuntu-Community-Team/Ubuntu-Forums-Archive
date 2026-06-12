---
title: "Scripts and MIME types"
date: 2006-05-20
forum: Desktop Environments
---

### Post by Nonno Bassotto on 2006-05-20
Is there a way to make Nautilus display scripts on a MIME type basis (as you can do in KDE)? I thought there wasn't a way until i found
[http://www.osnews.com/story.php?news_id=5361](http://www.osnews.com/story.php?news_id=5361)
where I can read
[HTML]
Nautilus supports script addons that apply certain actions on the selected files or on the currently open folder. It also has a MIME backend and so certain actions only happen to the correct files.
[/HTML]
This would be REALLY useful, because it would allow you to put far more scripts in your folder (of course you can do this, but then you lose more time in searching the right script than you would lose doing things by hand).

PS I know of Nautilus-actions
[http://www.grumz.net/?q=](http://www.grumz.net/?q=)
but scripts are much more powerful and customizable.

---

### Post by adamkane on 2006-05-20
As the article explains, Nautilus needs to be rewritten.

For now, you would need a Nautilus script that creates a menu (using zenity) of scripts according to the mime-type of the file. 

You would need to store your scripts in a separate folder, and have the exec-by-mime-type script search for any scripts that could be run on the selected file/files.

Not very elegant.

---

### Post by Nonno Bassotto on 2006-05-21
Could you be more detailed in what you describe? How can I make a nautilus script affect nautilus menu? I'm not very expert on scripting. I know, this would be a dirty hack, but if it works, it will be worth the pain :rolleyes: .
I think that this script-by-mime thing would be a great improvement in gnome usability. You would get lots of new functions in nautilus with little effort by the gnome dev team. I don't understand why the priority is low on bugzilla ](*,) .

---

