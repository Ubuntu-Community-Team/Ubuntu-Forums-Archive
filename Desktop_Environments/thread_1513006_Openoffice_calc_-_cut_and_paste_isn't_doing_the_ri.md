---
title: "Openoffice calc - cut and paste isn't doing the right thing"
date: 2010-06-18
forum: Desktop Environments
---

### Post by reuben on 2010-06-18
This is best explained with an example. Check out the attached spreadsheet. Column A's cells have formulas; A1 = B5+C5+D5, A2 = B6+C6+D6, etc.

Highlight C6 with your mouse, press ctrl X (or right click and cut), and paste into C8. You would expect the cell that references C8 (A4) to update, which it does; BUT, A2 also updates. And, if you now check the formula in A2, it has changed to B6+C8+D6. 

Is this a setting or a bug? If it's a setting, how do I turn it off? It's very annoying.

---

### Post by Hagar Delest on 2010-06-19
Seems rather logical for me. If you've created a link to a cell, you can expect the application to keep that link when you move the cell. Else, it would mean that your sheet cannot be changed anymore, preventing the user to move cells to change the layout.

If you want to avoid that, copy and paste the cell to get the value and then go back to the cell and delete its content.

---

