---
title: "[SOLVED] Extend gedit to open URLs in default browser?"
date: 2008-02-06
forum: Desktop Environments
---

### Post by MountainX on 2008-02-06
Is is possible to extend gedit to open plain text URLs in the default browser?

I would like to have gedit work so that when the cursor is in a url (such as [www.ubuntuforums.org](www.ubuntuforums.org), either with "http://" or just "www.") it can select that URL, pass the URL to the browser, and have the browser open that URL -- or open it in a new tab (if the browser is already open).

I need a simple solution. I'm not ready to write a plugin for gedit from scratch -- not even close. I'm still learning Ubuntu.

---

### Post by MicahCarrick on 2008-02-06
You can use the External Tools plugin. A simplified version (doesn't check for www or http) could work as follows:

1. Create a new external tool... something like "Jump to URL".
2. Set the command to:
```
xargs -I '{}' firefox '{}'
```
3. If you want, set a shortcut key.
4. Set the input to "Current Word"

With this tool, you can go to 'Tools' > 'Jump to URL' and firefox will launch and try to navigate to the URL (or word) under the cursor in Gedit.

---

### Post by MicahCarrick on 2008-02-06
PS. Doing a simple shell script with something like grep you could first check for http:// or www.

---

### Post by MountainX on 2008-02-06
Those are good suggestions... And using gnome-open instead of firefox will cause it to open in the default browser.

However, the tricky part seems to be how to utilize a regex to expand the current word to a selection that represents a full URL. That's the part that doesn't seem like it will work...

---

### Post by MountainX on 2008-02-06
Here's what I did to get a very basic version working:

1. selected the external tools plugin in gedit
2. Defined a new tool with these values:
[LIST]
[*]name: "Launch in browser"
[*]description: Open selected URL in browser
[*]shortcut key: <Control>semicolon
[*]command: xargs -I '{}' gnome-open '{}'
[*]input: current selection
[*]output: display in bottom pane
[*]Applicability: local files only
[/LIST]

To use it, select the URL and type the shortcut key. It opens the link in a new tab in the default browser (firefox for me).

Now, how the heck can I make it more intelligent so I don't have to select the URL manually?

I think the regex for URI's is like this:
```

"((([a-zA-Z][0-9a-zA-Z+\\-\\.]*):)?/{0,2}[0-9a-zA-Z;:,/\?@&=\+\$\.\-_!~\*'\(\)%]+)?(#[0-9a-zA-Z;,/\?:@&\=+$\.\\-_!~\*'\(\)%]+)?"


```
[http://www.apps.ietf.org/rfc/rfc2396.html](http://www.apps.ietf.org/rfc/rfc2396.html)

---

