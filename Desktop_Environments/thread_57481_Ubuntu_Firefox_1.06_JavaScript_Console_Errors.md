---
title: "Ubuntu Firefox 1.06 JavaScript Console Errors"
date: 2005-08-16
forum: Desktop Environments
---

### Post by Gagnefury on 2005-08-16
I installed the latest version of flash and I am trying to view ESPN motion highlights. 

[http://espn.go.com/](http://espn.go.com/)

Error: flash1_DoFSCommand is not defined
Source File: javascript: function jsScriptObject(obj) { this.wrappedJSObject = obj; } jsScriptObject.prototype = { evaluate : function(expression) { return new jsScriptObject(eval(expression)); } }; var plugin = document.embeds['flash1']; plugin.SetWindow(new jsScriptObject(window),13849);
Line: 1

XML Parsing Error: no element found
Location: jar:resource:///chrome/toolkit.jar!/content/mozapps/update/updates.xml
Line Number 1, Column 1:

XML Parsing Error: no element found
Location: jar:resource:///chrome/toolkit.jar!/content/mozapps/update/updates.xml
Line Number 1, Column 1:

Error: uncaught exception: [Exception... "Component returned failure code: 0x80570009 (NS_ERROR_XPC_BAD_CONVERT_JS) [nsIXPCComponents.lookupMethod]"  nsresult: "0x80570009 (NS_ERROR_XPC_BAD_CONVERT_JS)"  location: "JS frame :: chrome://global/content/XPCNativeWrapper.js :: anonymous :: line 91"  data: no]

Error: uncaught exception: [Exception... "Component returned failure code: 0x80570009 (NS_ERROR_XPC_BAD_CONVERT_JS) [nsIXPCComponents.lookupMethod]"  nsresult: "0x80570009 (NS_ERROR_XPC_BAD_CONVERT_JS)"  location: "JS frame :: chrome://global/content/XPCNativeWrapper.js :: anonymous :: line 91"  data: no]

Error: uncaught exception: [Exception... "Component returned failure code: 0x80570009 (NS_ERROR_XPC_BAD_CONVERT_JS) [nsIXPCComponents.lookupMethod]"  nsresult: "0x80570009 (NS_ERROR_XPC_BAD_CONVERT_JS)"  location: "JS frame :: chrome://global/content/XPCNativeWrapper.js :: anonymous :: line 91"  data: no]

Error: uncaught exception: [Exception... "Component returned failure code: 0x80570009 (NS_ERROR_XPC_BAD_CONVERT_JS) [nsIXPCComponents.lookupMethod]"  nsresult: "0x80570009 (NS_ERROR_XPC_BAD_CONVERT_JS)"  location: "JS frame :: chrome://global/content/XPCNativeWrapper.js :: anonymous :: line 91"  data: no]


I am also trying to view [www.dodgers.com](www.dodgers.com) and alot of the formatting on the webpage is off. I am unable to view some text and some objects are off centered. Any help would be appreciated, I've tried uninstalling and reinstalling firefox and I get the same results.

---

### Post by Gagnefury on 2005-08-16
bump

---

### Post by Gagnefury on 2005-08-19
double bump, anybody know?????  ](*,)   ](*,)   ](*,)   :???:

---

### Post by xaque on 2005-08-19
I had a similar problem, and it was fixed by opening Synaptic and reinstalling the packages "mozilla-firefox" and "mozilla-firefox-gnome-support". Dunno why this fixed it but it did. Hope that helps.

---

### Post by Gagnefury on 2005-08-20
Are you able to view the webpages correctly I mentioned above?

---

### Post by garak on 2005-09-09
[QUOTE=Gagnefury]Are you able to view the webpages correctly I mentioned above?[/QUOTE]
I have same problem too.
I checked the site you mentioned, it seems to be displayed correctly.

Anyway, almost any site I visit causes javascript console to be filled with errors :|

---

### Post by sjmorgan on 2005-09-09
Please report your experiences here: [http://bugzilla.ubuntu.com/show_bug.cgi?id=12124](http://bugzilla.ubuntu.com/show_bug.cgi?id=12124)

---

### Post by garak on 2005-09-29
A small update: after upgrading to 1.0.7, errors are much much less.
Didn't disappear, but now are very few :)

---

### Post by bdn01 on 2005-10-05
I'm using 1.07 and get the same error:

"Error: uncaught exception: [Exception... "Component returned failure code: 0x80570009 (NS_ERROR_XPC_BAD_CONVERT_JS) [nsIXPCComponents.lookupMethod]"  nsresult: "0x80570009 (NS_ERROR_XPC_BAD_CONVERT_JS)"  location: "JS frame :: chrome://global/content/XPCNativeWrapper.js :: anonymous :: line 91"  data: no]"

I have some javascript that may be causing this:

function xmlHttp(action) {
    if (document.getElementById('login') == null ) {
     var xmlhttp=false;
     var url='http://localhost:8080/ws/home';    

      try {
        xmlhttp = new ActiveXObject("Msxml2.XMLHTTP");
      } catch (e) {
        try {
          xmlhttp = new ActiveXObject("Microsoft.XMLHTTP");
       } catch (E) {
         xmlhttp = false;
       }
      } 

     if (!xmlhttp && typeof XMLHttpRequest!='undefined') {
       xmlhttp = new XMLHttpRequest();
     }

      xmlhttp.open("GET", "?action=" + action, true);
      xmlhttp.onreadystatechange=function() {
        if (xmlhttp.readyState==4) { 
 	 var newDiv = document.createElement('div');
 	 newDiv.innerHTML = xmlhttp.responseText;
         bodyRef = document.getElementsByTagName("body").item(0);
  	 bodyRef.appendChild(newDiv);
        }
      }
      xmlhttp.send(null)
     }
}

---

