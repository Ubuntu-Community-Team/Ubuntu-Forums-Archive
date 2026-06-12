---
title: "OpenOffice Spreadsheet - Total All &quot;Numerical&quot; Values in a Column"
date: 2009-05-01
forum: General Help
---

### Post by gerowen on 2009-05-01
I recently bought a new computer that shipped with Window$ Vista on it, so I used it for a little while just to see what it was all about. Then I heard Ubuntu was releasing a new version and I backed up all my documents and installed it, and I'm quite pleased and plan on keeping it as my permanent OS. However, I have an issue. I use a spreadsheet to manage my checking account, every deposit or withdrawal all the way from a stick of gum to paying the rent gets tracked on this thing, and I have a sheet for each month to kind of help with organization. At the top right of the sheet, to the right of all my normal columns, I put two cells labeled "Total Withdrawals" and "Total Deposits" that automatically update to show me at a glance my total withdrawals and total deposits for the month so I can make sure that I keep my input greater than my output. In MS Excel, the formula "=SUM(B:B)" set the value of the cell to the total of all numerical values in column B. This formula doesn't work however in OpenOffice. The first cell of column B is the label "Withdrawal Amount", so I just want it to total all of the numerical value cells in column B. Anybody know what formula I would use for this in OpenOffice?

---

### Post by roger_1960 on 2009-05-01
Hi

=SUM(B1:B1000)

should work?  It ignores text entries.

---

