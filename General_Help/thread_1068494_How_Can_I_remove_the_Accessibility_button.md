---
title: "How Can I remove the Accessibility button ?"
date: 2009-02-13
forum: General Help
---

### Post by fprg on 2009-02-13
Hi,I want to remove the  Accessibility button on the first win in wubi setup. The button almost never used,but may waste the time of user.I Can not find the source code related to the button and only see code lines below:

> !insertmacro MUI_RESERVEFILE_INSTALLOPTIONS ;InstallOptions.dll
Page custom ShowAccessibilityPage LeaveAccessibilityPage
!define MUI_PAGE_CUSTOMFUNCTION_PRE WelcomePagePre
!define MUI_PAGE_CUSTOMFUNCTION_SHOW WelcomePageShow
!define MUI_WELCOMEPAGE_TITLE $(CDBootTitle)
!define MUI_WELCOMEPAGE_TEXT $(CDBootText)
!insertmacro MUI_PAGE_WELCOME
Page custom ShowMainPage LeaveMainPage  ;in main_page.nsh

Can anyone help me remove the Accessibility button?

---

### Post by brandon88tube on 2009-02-13
Can you explain this more as I have no idea what you are talking about. Maybe a screenshot would help. I probably won't be of any help in this case, but it caught my attention and I am now curious as to what you are talking about.

---

### Post by fprg on 2009-02-13
Aha,I mean the Access button. I want to remove it.
I have found a way: add "BackEnabled=0" to main_page.ini [setting] section. Then the button come to unenbled,but visible. The best,hide it.

---

