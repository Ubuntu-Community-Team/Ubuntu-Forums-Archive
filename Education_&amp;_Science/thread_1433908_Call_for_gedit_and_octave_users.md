---
title: "Call for gedit and octave users"
date: 2010-03-19
forum: Education &amp; Science
---

### Post by carandraug on 2010-03-19
[SIZE="5"][COLOR="Red"]EDIT -- This is now part of gtksourceview so future versions of gedit will have it[/COLOR][/SIZE]

Hi

I've been changing the file that takes care of octave syntax highlight in gedit (syntax highlight is taken care by gtksourceview so I'm guessing other text editors may also use it) and I plan on giving it to the developers but I'd like have some opinions/test from other users too.

I am still but a basic user of octave (I only started a month ago) so I would appreciate if other users, that probably have much better code with all kind of tricks, could give it a go and say if everything still looks good when they try the strange things.

In gtksourceview, every file has its own 'lang' file which defines the syntax highlight of that language. It's basically a bunch of regular expressions, in a XML file, pointing to different styles of formatting.

The file is attached (I had to archive into a tar to upload into the forum). To give it a try, move it into the folder
```
/usr/share/gtksourceview-2.0/language-specs
```
You may want to backup up the old one first but if you don't, the file that is being distributed at any time, can be [found here]("http://git.gnome.org/browse/gtksourceview/plain/gtksourceview/language-specs/octave.lang").

Here's a list of changes I made to the original file:

[LIST]
[*]comments and continuation line
[LIST]
[*]... is now identified as a continuation line character
[*]comments after the continuation line character do not disrupt it's highlight
[*]continuation lines characters are ignored if they are between single quotes
[/LIST]
[*]shebang line
[LIST]
[*]now it's defined by the default configuration as being such instead of just a comment
[/LIST]
[*]block comments
[LIST]
[*]added #{ and #} to the list of possibilities for block comments
[*]highlights correctly when block comments are nested
[/LIST]
[*]operators
[LIST]
[*]now are highlighted (not only simple arithmetic operators, this includes element by element, transpose operator, autoincrement, assignment and logical operators)
[/LIST]
[*]functions
[LIST]
[*]added a bunch of functions (I was told by one of the previous developers of this file the reason why only a few functions were highlighted. The thing is that with time, some functions are deprecated and removed from octave. However, the gtksourceview developers won't remove them from the list of highlighted functions to maintain backward compatibility. That's understandable, so I only picked functions that also exist in Matlab which is already a much larger number than the before)
[*]just to make it look pretty I mixed some very similar functions into one such as "(a)?sin(d|h)?"
[*]removed 'ans' from the list of functions and highlighted it as a variable
[/LIST]
[*]metadata (it's the block that tells the text editor what to do when you for example automatically comment a line)
[LIST]
[*]added start and end of block comments start to the list (can someone test this please? I don't know a text editor that uses this)
[*]changed default for line comment from % to # (as asked from one of octave developers)
[/LIST]
[*]pkg as preprocessor
[LIST]
[*]if pkg is not called 'like a function' (i.e. pkg ("load",..)) it's highlighted as preprocessor (in similarity to the 'use' function in Perl)
[/LIST]
[*]constants/functions
[LIST]
[*]functions such as Inf, pi, NaN which can be called with no arguments to return a constant value, are highlighted as constants in those situations but still as functions if followed by opening parenthesis
[/LIST]
[*]data types
[LIST]
[*]the function handle character '@' is now highlighted
[/LIST]
[*]true/false as functions
[LIST]
[*]are highlighted as boolean unless followed by opening parenthesis, in which case are highlighted as functions
[/LIST]
[*]keywords
[LIST]
[*]added the keywords, persistent, replot, static, varargin, varargout
[*]removed the keywords assert, nargin, nargout and moved them to be highlighted as functions
[/LIST]
[*]strings
[LIST]
[*]added a printf regexp that should identify its formatting (copied it from the C.lang file)
[*]added an escape regexp that should escape only some stuff, not whatever's right after an \ (also copied it from the C.lang file)
[/LIST]
[/LIST]

Note: some of the changes I made most likely won't have any impact visually. For example, previously, the shebang line was highlighted as just a comment. But the default file has a style specific for it so I changed. However, the style for the shebang line is sometimes the same as the style for comments so you may not see a difference (I know I don't).

Any opinion and testing will be most welcome. Please say something, even if just to say that it works good so I know it has been tested.
Thanks in advance

[SIZE="3"][COLOR="Red"]EDIT 1[/COLOR][/SIZE]: Changed the attachment for my latest octave.lang file
[SIZE="3"][COLOR="Red"]EDIT 2[/COLOR][/SIZE]: Changed the attachment again to support classes
[SIZE="3"][COLOR="Red"]EDIT 3[/COLOR][/SIZE]: Added attachment for octave 3.4
[SIZE="3"][COLOR="Red"]EDIT 4[/COLOR][/SIZE]: Added note that was finally added to gtksourceview trunk

---

### Post by carandraug on 2010-03-23
*bump*

---

### Post by carandraug on 2010-04-18
Made a few more changes, including highlight data type functions and function handles. Also if a struct field that has the same name of a function, will no longer be highlighted as function.

---

### Post by ad_267 on 2010-04-18
It works really well for me thanks, I couldn't find any problems with it. I don't think I do anything very advanced though.

---

### Post by nadeem.ansari on 2010-06-22
I moved the untar-ed file in the specified folder, and nothing changed. Still no highlighting for octave .m files.

gvim works great with octave after following the instructions here: 
[http://www.vim.org/scripts/script.php?script_id=1591](http://www.vim.org/scripts/script.php?script_id=1591)
However, I was looking something for gedit?

N.

---

### Post by carandraug on 2010-06-22
> **nadeem.ansari said:**
> I moved the untar-ed file in the specified folder, and nothing changed. Still no highlighting for octave .m files.

gvim works great with octave after following the instructions here: 
[http://www.vim.org/scripts/script.php?script_id=1591](http://www.vim.org/scripts/script.php?script_id=1591)
However, I was looking something for gedit?

N.

Make sure you have gtksourceview installed
```

sudo apt-get install libgtksourceview2.0-0
```

Then, untar this file in the mentioned directory

```
/usr/share/gtksourceview-2.0/language-specs

```

Finally, open an octave file in gedit and if it's not highlighted (or incorrectly highlighted), go to the menu

View --> Highlight mode --> Scientific --> Octave

---

### Post by liviogasp on 2010-07-30
Thank you carandraug, I'm using your file, much better than the one suited with ubuntu. I use also qtoctave and it's editor, but there is sometihng wrong, cause the blank space is not as large as the monospace character in that, and sometimes it has a strange behavior! How do you use octave? Simply terminal + gedit?

---

### Post by carandraug on 2010-07-30
> **liviogasp said:**
> Thank you carandraug, I'm using your file, much better than the one suited with ubuntu.

The one suited with Ubuntu is the one that the gtksourceview developers have available. I already submitted the patch but they haven't act on it yet. Could you consider comment on [this bug report]("https://bugzilla.gnome.org/show_bug.cgi?id=613378") saying that you approve of the patch? Just to try and get some attention from the developers.

> **liviogasp said:**
> How do you use octave? Simply terminal + gedit?

Yes. I find gedit to be a great text editor, no matter what the CLI purists may say. You can use the embedded terminal plugin if you don't want to keep Alt-Tab between the octave console and the text editor.

---

### Post by carandraug on 2010-10-15
I've changed the attachment. This new octave.lang file has support for classes (which among other things, allows the spell checker to be active only on strings). It also fixes a small bug where '' in single quotes was identified has end a start of a new string instead of an escaped single quote.

Hopefully it will also be useful for other users.

---

### Post by carandraug on 2011-04-01
Added a new lang file for the new octave 3.4. It highlights some of the new functions
[LIST]
[*]curl
[*]daspect
[*]divergence
[*]erfcx
[*]fileread
[*]fminbnd
[*]merge
[*]onCleanup
[*]pbaspect
[*]pie3
[*]randi
[*]reset
[*]rsf2csf
[*]saveas
[*]strread
[*]textread
[*]uigetdir
[*]uigetfile
[*]uimenu
[*]uiputfile
[*]whitebg
[/LIST]

Also removed the following functions from highlight since they have been removed or deprecated (will be removed on 3.6 or 3.8).
[LIST]
[*]setstr
[*]str2mat
[*]values
[/LIST]

I also added the class keyword to the keywords group.

---

