---
title: "Changing default mail client"
date: 2004-11-29
forum: Desktop Environments
---

### Post by artAlexion on 2004-11-29
I want to change the default mail client so that Mozilla Thunderbird starts on mail links  rather than Evolution.

I tried making the changes in the Preferred Applications app, but when I try to do a "Send Page" in Firefox, I get the error
[INDENT]Error launching browser window:TypeError:[/INDENT] [INDENT]Components.classes['@mozilla.org/appshell/component/browser/instance;1'] has no properties[/INDENT] 

What other changes do I need to make?

---

### Post by wazoo on 2004-12-24
Yep, same problem here. Evolution is a dandy application, but chokes repeatedly on a Palm sync -- duplicating blank entries, wiping out my /dev/pilot file, not transferring categories, etc. Enough! I installed JPilot, and it works everytime, no surprises.

Here's something I HAVE learned about Thunderbird. 

Computer>Desktop>Preferred Applications>Mail Read>mozilla-thunderbird %s

WILL open a mailto link from a website, but ONLY if Thunderbird is NOT already running. Try it.

And I sure would like to know how to fix that! Otherwise, you have to cut and paste from Firefox to Thunderbird. Mozilla/Mozilla-Mail was easier!

---

### Post by hardcandy on 2004-12-24
I have not tried this, so no guarantees.
Type "about:config" in the Firefox address window. Press enter.
Go to the line, 
"network.protocol-handler.external.mailto  default  boorlean true" , right click on it and change "true" to "false". I do not have Thunderbird installed, so I can not test this.

---

### Post by artAlexion on 2004-12-25
[QUOTE=wazoo]Yep, same problem here. Evolution is a dandy application, but chokes repeatedly on a Palm sync -- duplicating blank entries, wiping out my /dev/pilot file, not transferring categories, etc. Enough! I installed JPilot, and it works everytime, no surprises.[/QUOTE]

Yeah.  Used jpilot in the past without problems.  This is my third try with evolution.  It always shows lots of promise, but in the end has some issue that makes it a no go for me.  I think it is overkill for my needs.  I just want a good mail client (MUA), not an outlook replacement.


[QUOTE=wazoo]Here's something I HAVE learned about Thunderbird. 

Computer>Desktop>Preferred Applications>Mail Read>mozilla-thunderbird %s[/QUOTE]

I did that before, all it seemed to accomplish was *not* using Evolution and bringing up an error instead.

[QUOTE=wazoo]WILL open a mailto link from a website, but ONLY if Thunderbird is NOT already running. Try it.[/QUOTE]

I didn't notice this.  Will have to try with T-bird not running.

---

### Post by artAlexion on 2004-12-25
[QUOTE=hardcandy]I have not tried this, so no guarantees.
Type "about:config" in the Firefox address window. Press enter.
Go to the line, 
"network.protocol-handler.external.mailto  default  boorlean true" , right click on it and change "true" to "false". I do not have Thunderbird installed, so I can not test this.[/QUOTE]

Mine was already set to false.  I tried setting it to true.

---

