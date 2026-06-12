---
title: "email filtering on maildir archive - fo use with offlineimap"
date: 2008-12-29
forum: General Help
---

### Post by hexamon on 2008-12-29
Hello,
  I am re-vamping my email flow and wanted to solicit opinions.

**Old-setup**
  imap via thunderbird archiving to Local-Folders.

**New-setup**
  imap-->offlineimap-->maildir-->mutt

**Dream-setup**
  imap-->offlineimap-->gmail.  Unfortunately, offlineimap does not support gmail as a IMAP-destination; gmail is only supported as an IMAP-source.  One of my restrictions is that I can not set up forwarding to my gmail account; otherwise that would have been a solution.


**Reason for switching**
  Thunderbird was getting bogged down with the ~800 email or so that I get a day from lists and automated alert systems. I don't read most of these alerts but I need to keep them for reference at least a 1 month.

**Questions**
 Is there an easy way to filter existing maildir archives on a file system?  Here are the options I was able to come up with.

**Options:**
1. Create a mutt macro (or folder hook) that runs the following command
```
`for file in ~/Mail/INBOX/cur/*; do formail -s procmail < $file;done`
```
---CON: This is cumbersome because I need two versions depending on whether I want the operation to run on new versus non-new.  This can't *move messages*, it can only *copy them*.
---PRO: I can use procmail with robust filtering.

2. Create mutt macros that tag and save off based on list@ or subject, etc.
---CON: I need a macro for every type of list, or any set of messages that go to a common folder.  I have to remember each macro and run it.  I could create a folder hook, but there is no logging of events, so interactive seems the safer way to go.

3. Use Evolution on local maildir archive and create evolution filters.  Why not Thunderbird with the local archive?  Thunderbird doesn't support maildir format as a local folder.  Why use maildir?  offlineimap only supports maildir.
---CON: create tons of non portable filters and learn a new (kinda slow) gui and gotchas of a new application.
---PRO: Will be relatively easy to create and maintain filters.

4.  Use some offlineimap trickery and setup the same folder structure from IMAP on gmail, then:
IMAP-->offlineimap-->localMaildir-->offlineimap-->gmail.
---CON: self evident
---PRO: I get to use gmail and don't need filters any more.  Just tag my way to happiness.

Any other options for filtering on a maildir repo?  Any innput, thoughts or ideas?

Thanks

---

### Post by hexamon on 2008-12-30
One last bump before giving up.  Any good maildir filtering tools out there?

---

