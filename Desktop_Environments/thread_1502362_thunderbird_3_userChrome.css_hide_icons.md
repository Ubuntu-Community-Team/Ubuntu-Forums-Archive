---
title: "thunderbird 3 userChrome.css hide icons"
date: 2010-06-05
forum: Desktop Environments
---

### Post by xegroeg on 2010-06-05
i want to hide all icons in thunderbird 3.  i've changed the title bar to text only, but the folder tree and tabs i cannot.  i was able to do this in firefox by creating a userChrome.css file and specifying what i want there.  

the userChrome.css file doesn't work in thunderbird and i'm having trouble locating code examples particular to tbird.  

any suggestions or other methods to achieve thunderbird iconlessness :D?

---

### Post by xegroeg on 2012-08-11
> **xegroeg said:**
> i want to hide all icons in thunderbird 3.  i've changed the title bar to text only, but the folder tree and tabs i cannot.  i was able to do this in firefox by creating a userChrome.css file and specifying what i want there.  

the userChrome.css file doesn't work in thunderbird and i'm having trouble locating code examples particular to tbird.  

any suggestions or other methods to achieve thunderbird iconlessness :D?

Hello, old self.  Here ya' go.  Please vi ~/.thunderbird/*/chrome/userChrome.css and insert:

/*
  * Do not remove the @namespace line -- it's required for correct functioning
  */
 @namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul"); /* set default namespace to XUL */

/* Kill all tab icons, no matter what */
.tabbrowser-tabs .tab-icon {
  display: none !important;
}

.textbox-search-icon {
  display: none !important;
}

.qfb-unread {
  display: none !important;
}

.emailStar {
  display: none !important;
}

/*treechildren::-moz-tree-image(flaggedCol) {
  -moz-image-region: rect(0px 16px 16px 0px) !important;
}

treechildren::-moz-tree-image(flaggedCol, flagged) {
  -moz-image-region: rect(80px 16px 96px 0px) !important;
}
*/

#throbber-box {
    display: none !important;
}
/* Hide Tabbar close Button */ 
tabbrowser .tabs-closebutton-box { 
    display: none !important; 
}

/* No Mail Folder Icons */
treechildren::-moz-tree-image(folderNameCol) {
    margin-right: 0px;
    list-style-image: none !important;
    margin-left: -15px !important;
}
    
treechildren::-moz-tree-image(subjectCol) {
    list-style-image: none !important; 
}

#threadTree > treechildren::-moz-tree-cell-text(subjectCol) {
    -moz-margin-start: -5px !important; 
    -moz-margin-end: 5px !important; 
}

#threadTree treechildren::-moz-tree-row(odd) {
      background-color: transparent !important;
}

#threadTree treechildren::-moz-tree-row(odd, selected) {
        background-color: Highlight !important;
}


..and in ~/.thunderbird/*/chrome/userChrome.js:

// make account and folder names available to userChrome.css
 with (document.getElementById("folderNameCell"))
    setAttribute("properties", getAttribute("properties") + " name-?folderTreeName")

---

### Post by wildmanne39 on 2012-08-11
Thanks for sharing. Thread Closed.

---

