---
title: "OpenOffice Headings don't appear in Navigator or  ToC"
date: 2007-03-13
forum: Desktop Environments
---

### Post by daengbo on 2007-03-13
Using a basic install of 6.10. No modifications.

Because I prefer it for simple work, I wrote out a short report in Abiword, then was asked to use it to make a longer one, so I exported to ODF and started using OpenOffice, so that . The format was a little strange, so I changes everything to Default and removed all formatting, then reformatted it (using all styles, of course).

The problem is that I have only a single item showing up in Navigator -- a Heading 3 item. None of the other fifteen or so headings appear, though I can change the heading style and everything updates normally.

Has anyone ever encountered this? Ways to work around it other than exporting to text and starting over? There are too many tables for me to do that ....

---

### Post by ingo on 2007-11-15
just happened to me but found no solution yet. will keep on searching

---

### Post by ppedrok on 2008-01-25
I had a similar problem: In my Navigator window, all headings showed, except Heading 1.
I found instructions in [http://www.oooforum.org/forum/viewtopic.phtml?t=16255]("http://www.oooforum.org/forum/viewtopic.phtml?t=16255") that helped me. "ftack" wrote:

> *Indeed, your headings must have been formatted using specific styles before there is a change of seeing them in navigator. The default Word heading styles will translate to the default writer heading styles. If other styles were used in the Word document, then you can tell Writer to recognise these specific styles as the Heading styles for your current document. to that aim, open Tools - outline numbering. Click level 1, then under Paragraph style, select the paragraph style that actually is being used for formatting the Heading 1 styles. Adjust that for each level. Now, your custom styles will be "promoted" to be the Outline styles.*

I looked at Tools - outline numbering, and behold: level 1, chapter style was set to none. All the others had their corresponding chapter style set. I set the chapter style of outline numbering, level 1 to Heading 1, and problem solved! :)
I hope this helps you also.
Cheers!

---

