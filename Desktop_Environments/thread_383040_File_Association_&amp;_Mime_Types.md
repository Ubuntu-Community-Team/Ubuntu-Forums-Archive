---
title: "File Association &amp; Mime Types?"
date: 2007-03-12
forum: Desktop Environments
---

### Post by alexgieg on 2007-03-12
Hi!

I'm using Ubuntu for some days now, and I found a small annoyance. What happens is that I am a heavily user of .lua and .toc text files (used for World of Warcraft extensions) and thus I'd like to have them opening in gEdit when I double-click them on Nautilus. However, I found no way to associate the double-clicking of files with these extensions with gEdit. I followed some how-tos I found on creating new mime-types and the like, but they didn't work, and as a result Nautilus keeps complaining that it's "impossible" to open these files in gEdit because that might be insecure (how opening a plain text file in a plain text editor could be a security risk, I don't know).

What's the easiest way to accomplish this somewhat simple task? I've read comments on giving up on Nautilus and installing Konqueror instead, but I don't want to follow that path. I really prefer getting a deeper understanding on how Nautilus works.

If someone could provide me a simple step-by-step set of instructions that would allow me to associate text files with arbitrary extensions to gEdit in Nautilus double-clicking, I'd would be very thankful!

Alexander

---

### Post by alexgieg on 2007-03-13
Sorry to insist, but does no one know how to do this? :(

---

### Post by mannheim on 2007-03-14
I'll have a go. I think there are two issues here.[LIST=1]
[*]How to get Nautilus to open a given type of file (mime type) with the Application of your choice.
[*]How to alter how gnome decides what mime type a given file is.
[/LIST]

The first is easy, and maybe you have already tried this. Right-click on a file of the relevant type, select Properties from the pop-up menu, and then select the "Open With" tab. If the relevant App appears on the list there, just select it. Otherwise, click "Add" and add the command-line for the relevant application.

That said, I think your problem is more of the second type above. Gnome looks at the file extension and (at some point) the contents of the file to determine the mime type. If the extension leads it to believe the file is of one type but the contents indicate another type, then the user interface warns you of a possible threat -- and yes, I think Nautilus is ridiculously over-zealous in not letting you proceed.

A first question is, what mime-type does Nautilus believe these files are? Is it text/plain? (Look in "Properties".) If it believes they are not plain text when trying to open them, what might be the content of the file that raises a flag?

If all else fails, you can change the rules that Gnome uses to decide what mime type a file belongs to, but it is hard. To do this system-wide, you need to create and edit (as root) a file:
```
sudo gedit /usr/share/mime/packages/Overrides.xml
```
I think you can also do it on a per-user basis by editing the user's file:
```
gedit ~/.local/share/mime/packages/Overrides.xml
```

What you put in the Overrides.xml file is tougher. There is some guideline [here]("http://www.gnome.org/learn/admin-guide/latest/mimetypes-modifying.html"), and by looking at the other files in the packages directory under share/mime. Here's an example:

```
  
  <mime-type type="application/pdf">
    <comment>PDF document</comment>
    <magic priority="50">
      <match value="%PDF-" type="string" offset="0"/>
    </magic>
    <glob pattern="*.pdf"/>
    <alias type="application/x-pdf"/>
  </mime-type>

```

This chunk of code, as part of one of the xml files, tells gnome that PDF files can be recognized by having a filename of pattern "*.pdf" and having a content which contains the magic string "%PDF-" at offset 0 (i.e. at the beginning of the file. Each rule has a priority, 1-100, I think.
The xml file has to begin and end with:

```
<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
    ....
</mime-info>

```

After creating the xml file, you need to run
```
sudo update-mime-database /usr/share/mime/
```
or
```
 update-mime-database ~/.local/share/mime/
```

I would  be very glad if someone on this forum told me a simpler way to do any or all of this!

---

### Post by alexgieg on 2007-03-14
Thanks for the long reply. It is a lot of work, but I'll try to do it and, if successful, will attempt submitting the two new mime-type definitions to whoever is responsible for including them. By the way, do you know who that would be?

Regarding your questions: right-clicking and selecting "open with" works. The problem is when I double-click the file. The error message says the files was detected as plain text, but the extension (.toc or .lua) isn't the one expected for plain-text files (.txt), so it won't open it in the default application for plain text files.

Maybe a solution would then be to edit the Overrides.xml file to merely add other extensions in the "glob" entry for plain text definition. I'll try that when I'm back at home and see what happens.

By the way, I really think Nautilus should allow for simpler overriding of these security settings. An "always allow for this file type" check mark option in the warning window wouldn't hurt, provided it only applied to the local user and was grayed out for any sudoed Nautilus session. Not having this is a serious lack of usability. Where's the proper place to make this suggestion?

---

### Post by mannheim on 2007-03-14
I think the correct place to put a feature request or bug report is in the [bug-reporting page]("https://bugs.launchpad.net/ubuntu/+filebug") on launchpad. It's not an ubuntu-specific problem, of course, but an "upstream" problem in gnome; but such bugs are supposed to be forwarded upstream by the ubuntu people. Whether anything happens after that ...

---

