---
title: "default browser in thunderbird"
date: 2012-07-12
forum: Desktop Environments
---

### Post by barna on 2012-07-12
Hi,
I would like to change the default browser that is opened from thunderbird from firefox to chrome. I have changed the kde system preferences to have chrome as the default browser, kde-open [http://.](http://.)... and xdg-open [http://.](http://.)... commands launch chrome, but thunderbird still launches firefox. 
I have added
user_pref("network.protocol-handler.app.http", "/usr/bin/firefox");
user_pref("network.protocol-handler.app.https", "/usr/bin/firefox");
user_pref("network.protocol-handler.app.ftp", "/usr/bin/firefox");
as suggested on the page [http://kb.mozillazine.org/Setting_Your_Default_Browser#Linux](http://kb.mozillazine.org/Setting_Your_Default_Browser#Linux)
without any result, thunderbird still launches firefox. If I uninstall firefox, then thunderbird launches chrome.

Do you have any suggestion?
Thanks
Daniel

---

### Post by spjackson on 2012-07-12
I am puzzled. If you are wanting to change the default browser from Firefox to Chrome, then why have you added user_pref entries for /usr/bin/firefox rather than /usr/bin/chromium-browser?

---

### Post by barna on 2012-07-12
Oh sorry, a stupid mistake: I copied these three lines into my question from that webpage, and not from my .js file. In that file I of course specified chrome :-)

---

### Post by spjackson on 2012-07-12
It seems that things are different in Thunderbird 3. I have successfully tried doing it this way [http://www.unicom.com/blog/entry/650](http://www.unicom.com/blog/entry/650)

---

### Post by barna on 2012-07-12
Hi,
Thanks for this hint. It does not work for me either, it still launches firefox without prompting me.

---

### Post by Lorin Ricker on 2012-08-28
> **spjackson said:**
> It seems that things are different in Thunderbird 3. I have successfully tried doing it this way [http://www.unicom.com/blog/entry/650](http://www.unicom.com/blog/entry/650)

Thanks -- This worked perfectly for me. -- Lorin

---

### Post by barna on 2012-09-06
Hi,
Doing whatever in the GUI config window of Thunderbird did not help. Also, there was no way to set up an external application for video/avi mime types in the GUI (I could not add any more mime types, actions, etc). It's a mess. Finally I removed the ~/.thunderbird/profilename/mimeTypes.rdf file and set it up manually like this, which works:
```

<?xml version="1.0"?>
<RDF:RDF xmlns:NC="http://home.netscape.com/NC-rdf#"
         xmlns:RDF="http://www.w3.org/1999/02/22-rdf-syntax-ns#">
  <RDF:Description RDF:about="urn:mimetypes">
    <NC:MIME-types RDF:resource="urn:mimetypes:root"/>
  </RDF:Description>
  <RDF:Description RDF:about="urn:schemes">
    <NC:Protocol-Schemes RDF:resource="urn:schemes:root"/>
  </RDF:Description>

  <!-- ################### list of known mime types ##################### -->
  <RDF:Seq RDF:about="urn:mimetypes:root">
    <RDF:li RDF:resource="urn:mimetype:image/png"/>
    <RDF:li RDF:resource="urn:mimetype:image/gif"/>
    <RDF:li RDF:resource="urn:mimetype:image/jpg"/>
    <RDF:li RDF:resource="urn:mimetype:application/pdf"/>
    <RDF:li RDF:resource="urn:mimetype:video/avi"/>
    <RDF:li RDF:resource="urn:mimetype:video/avi"/>
    <RDF:li RDF:resource="urn:mimetype:video/mp4"/>
    <RDF:li RDF:resource="urn:mimetype:audio/mp3"/>
    <RDF:li RDF:resource="urn:mimetype:application/msword"/>
  </RDF:Seq>

  <!-- ################### Description of known mime types  ############## -->
  <RDF:Description RDF:about="urn:mimetype:image/png"
                   NC:fileExtensions="png"
                   NC:description="PNG Image"
                   NC:value="image/png"
                   NC:editable="true">
    <NC:handlerProp RDF:resource="urn:mimetype:handler:image/png"/>
  </RDF:Description>
  <RDF:Description RDF:about="urn:mimetype:image/gif"
                   NC:fileExtensions="gif"
                   NC:description="GIF Image"
                   NC:value="image/gif"
                   NC:editable="true">
    <NC:handlerProp RDF:resource="urn:mimetype:handler:image/gif"/>
  </RDF:Description>
  <RDF:Description RDF:about="urn:mimetype:image/jpg"
                   NC:fileExtensions="jpg"
                   NC:description="JPG Image"
                   NC:value="image/jpg"
                   NC:editable="true">
    <NC:handlerProp RDF:resource="urn:mimetype:handler:image/jpg"/>
  </RDF:Description>
  <RDF:Description RDF:about="urn:mimetype:application/pdf"
                   NC:fileExtensions="pdf"
                   NC:description="PDF Document"
                   NC:value="application/pdf"
                   NC:editable="true">
    <NC:handlerProp RDF:resource="urn:mimetype:handler:application/pdf"/>
  </RDF:Description>
  <RDF:Description RDF:about="urn:mimetype:video/avi"
                   NC:fileExtensions="avi"
                   NC:description="AVI Video"
                   NC:value="video/avi"
                   NC:editable="true">
    <NC:handlerProp RDF:resource="urn:mimetype:handler:video/avi"/>
  </RDF:Description>
  <RDF:Description RDF:about="urn:mimetype:video/mp4"
                   NC:fileExtensions="mp4"
                   NC:description="MPEG-4 Video"
                   NC:value="video/mp4"
                   NC:editable="true">
    <NC:handlerProp RDF:resource="urn:mimetype:handler:video/mp4"/>
  </RDF:Description>
  <RDF:Description RDF:about="urn:mimetype:audio/mp3"
                   NC:fileExtensions="mp3"
                   NC:description="MP3 Audio"
                   NC:value="audio/mp3"
                   NC:editable="true">
    <NC:handlerProp RDF:resource="urn:mimetype:handler:audio/mp3"/>
  </RDF:Description>
  <RDF:Description RDF:about="urn:mimetype:application/msword"
                   NC:fileExtensions="doc"
                   NC:description="MS-Word Document"
                   NC:value="application/msword"
                   NC:editable="true">
    <NC:handlerProp RDF:resource="urn:mimetype:handler:application/msword"/>
  </RDF:Description>

  <!--  ########################### mimetypes-applications associations  ################### -->
  <RDF:Description RDF:about="urn:mimetype:handler:image/png"
                   NC:alwaysAsk="false"
                   NC:saveToDisk="false"
                   NC:useSystemDefault="false"
                   NC:handleInternal="false">
    <NC:externalApplication RDF:resource="urn:mimetype:externalApplication:image/png"/>
  </RDF:Description>
  <RDF:Description RDF:about="urn:mimetype:handler:image/jpg"
                   NC:alwaysAsk="false"
                   NC:saveToDisk="false"
                   NC:useSystemDefault="false"
                   NC:handleInternal="false">
    <NC:externalApplication RDF:resource="urn:mimetype:externalApplication:image/jpg"/>
  </RDF:Description>
  <RDF:Description RDF:about="urn:mimetype:handler:image/gif"
                   NC:alwaysAsk="false"
                   NC:saveToDisk="false"
                   NC:useSystemDefault="false"
                   NC:handleInternal="false">
    <NC:externalApplication RDF:resource="urn:mimetype:externalApplication:image/gif"/>
  </RDF:Description>
  <RDF:Description RDF:about="urn:mimetype:handler:application/pdf"
                   NC:alwaysAsk="false"
                   NC:saveToDisk="false"
                   NC:useSystemDefault="false"
                   NC:handleInternal="false">
    <NC:externalApplication RDF:resource="urn:mimetype:externalApplication:application/pdf"/>
  </RDF:Description>
  <RDF:Description RDF:about="urn:mimetype:handler:video/avi"
                   NC:alwaysAsk="false"
                   NC:saveToDisk="false"
                   NC:useSystemDefault="false"
                   NC:handleInternal="false">
    <NC:externalApplication RDF:resource="urn:mimetype:externalApplication:video/avi"/>
  </RDF:Description>
  <RDF:Description RDF:about="urn:mimetype:handler:video/mp4"
                   NC:alwaysAsk="false"
                   NC:saveToDisk="false"
                   NC:useSystemDefault="false"
                   NC:handleInternal="false">
    <NC:externalApplication RDF:resource="urn:mimetype:externalApplication:video/mp4"/>
  </RDF:Description>
  <RDF:Description RDF:about="urn:mimetype:handler:audio/mp3"
                   NC:alwaysAsk="false"
                   NC:saveToDisk="false"
                   NC:useSystemDefault="false"
                   NC:handleInternal="false">
    <NC:externalApplication RDF:resource="urn:mimetype:externalApplication:audio/mp3"/>
  </RDF:Description>
  <RDF:Description RDF:about="urn:mimetype:handler:application/msword"
                   NC:alwaysAsk="false"
                   NC:saveToDisk="false"
                   NC:useSystemDefault="false"
                   NC:handleInternal="false">
    <NC:externalApplication RDF:resource="urn:mimetype:externalApplication:application/msword"/>
  </RDF:Description>


  <!--  ####################### Selected action for the given mimetype ########## -->
  <RDF:Description RDF:about="urn:mimetype:externalApplication:image/png"
                   NC:prettyName="Gwenview"
                   NC:path="/usr/bin/gwenview" />
  <RDF:Description RDF:about="urn:mimetype:externalApplication:image/jpg"
                   NC:prettyName="Gwenview"
                   NC:path="/usr/bin/gwenview" />
  <RDF:Description RDF:about="urn:mimetype:externalApplication:image/gif"
                   NC:prettyName="Gwenview"
                   NC:path="/usr/bin/gwenview" />
  <RDF:Description RDF:about="urn:mimetype:externalApplication:application/pdf"
                   NC:prettyName="Okular"
                   NC:path="/usr/bin/okular" />
  <RDF:Description RDF:about="urn:mimetype:externalApplication:video/avi"
                   NC:prettyName="VLC"
                   NC:path="/usr/bin/vlc" />
  <RDF:Description RDF:about="urn:mimetype:externalApplication:video/mp4"
                   NC:prettyName="VLC"
                   NC:path="/usr/bin/vlc" />
  <RDF:Description RDF:about="urn:mimetype:externalApplication:audio/mp3"
                   NC:prettyName="VLC"
                   NC:path="/usr/bin/vlc" />
  <RDF:Description RDF:about="urn:mimetype:externalApplication:application/msword"
                   NC:prettyName="Libre Office"
                   NC:path="/usr/bin/libreoffice" />



  <!-- ########################## Schemes  ################################# -->

  <!-- #######################  List of known schemes  ##################### -->
  <RDF:Seq RDF:about="urn:schemes:root">
    <RDF:li RDF:resource="urn:scheme:http"/>
    <RDF:li RDF:resource="urn:scheme:https"/>
  </RDF:Seq>

  <!-- ###################### Description of schemes  ###################### -->
  <RDF:Description RDF:about="urn:scheme:http"
                   NC:value="http">
    <NC:handlerProp RDF:resource="urn:scheme:handler:http"/>
  </RDF:Description>
  <RDF:Description RDF:about="urn:scheme:https"
                   NC:value="https">
    <NC:handlerProp RDF:resource="urn:scheme:handler:https"/>
  </RDF:Description>

  <!-- #######################  Scheme handlers  ########################### -->
  <RDF:Description RDF:about="urn:scheme:handler:http"
                   NC:useSystemDefault="false"
                   NC:alwaysAsk="false">
    <NC:externalApplication RDF:resource="urn:scheme:externalApplication:http"/>
  </RDF:Description>
  <RDF:Description RDF:about="urn:scheme:handler:https"
                   NC:useSystemDefault="false"
                   NC:alwaysAsk="false">
    <NC:externalApplication RDF:resource="urn:scheme:externalApplication:https"/>
  </RDF:Description>

  <!--  ############################ External applications  ########################### -->
  <RDF:Description RDF:about="urn:scheme:externalApplication:http"
                   NC:prettyName="Chrome"
                   NC:path="/usr/bin/chromium-browser" />
  <RDF:Description RDF:about="urn:scheme:externalApplication:https"
                   NC:prettyName="Chrome"
                   NC:path="/usr/bin/chromium-browser" />


  <RDF:Description RDF:about="urn:root"
                   NC:en-US_defaultHandlersVersion="-1" />
</RDF:RDF>


```

---

