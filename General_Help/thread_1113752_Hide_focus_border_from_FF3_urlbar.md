---
title: "Hide focus border from FF3 urlbar ??"
date: 2009-04-01
forum: General Help
---

### Post by blacksm1th on 2009-04-01
How to hide focus border from FF urlbar? I use this code:
```
/* Hide gnome focus border around searchbar */
 	.searchbar-textbox 
		{ -moz-appearance:none!important; }
```
 to hide focus border from searchbar but i can't do the same for urlbar.
Here is the image:
[[IMG]http://img24.imageshack.us/img24/8906/screenshotubuntuforumsp.th.png[/IMG]](http://img24.imageshack.us/my.php?image=screenshotubuntuforumsp.png)

---

### Post by blacksm1th on 2009-04-06
I did an error asking and googling for "focus border" - it's a "highlight border". I fixed it with modified "WellRounded 3" code.
Final:
[img]http://img14.imageshack.us/img14/9514/screenshotubuntuforumsr.png[/img]

EDIT:  The code:
```
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul");

/**
* WellRounded 3
* v. 1.0.3pre4
* 2008-06-29 13:09 +0200
**/

	textbox:not([readonly]):not(.gtb-search-box), menulist 
		{ -moz-appearance: none !important;
		border: 2px solid !important;
		-moz-border-top-colors: rgba(0,0,0,0.70) threedshadow -moz-field !important;
		-moz-border-bottom-colors: rgba(0,0,0,0.40) threedshadow -moz-field !important;
		-moz-border-right-colors: rgba(0,0,0,0.56) threedshadow -moz-field !important;
		-moz-border-left-colors: rgba(0,0,0,0.51) threedshadow -moz-field !important;
		-moz-border-radius: 9.5pt !important;
		-moz-background-clip: padding !important; }

	textbox[focused="true"]:not(.gtb-search-box), menulist:focus
 		{ -moz-outline-radius: 9.5pt !important;
  		outline: none !important;
  		outline-color: rgba(60, 120, 240, 0.8) !important;
 		 outline-offset: -1pt !important; }


searchbar {
  min-height: 14pt !important;
}
searchbar textbox {
  padding-right: 2pt !important;
}
#urlbar:not(:-moz-system-metric(windows-default-theme)),
searchbar:not(:-moz-system-metric(windows-default-theme)) {
  margin-top: 0.8pt !important;
  margin-bottom: 1.5pt !important;
}
#urlbar, #urlbar>:not(#identity-box)>:not(dropmarker):not(progressmeter):not(.progress-bar), #urlbar>:not(#identity-box):not(#urlbar-icons), menulist dropmarker, menulist, textbox:not([readonly]), searchbar button {
  -moz-appearance: none !important; 
}
#urlbar:not([level]), #urlbar:not([level])>:not(#identity-box)>:not(dropmarker):not(progressmeter):not(.progress-bar), menulist dropmarker, menulist, textbox:not([readonly]):not([level]), searchbar button {
  background: -moz-Field !important;
}
#fission-status {
  opacity: 0.7 !important;
  background: -moz-Field !important;
  padding-left: 2pt !important;
  padding-right: 1.5pt !important;
}
textbox:not([empty="true"]):not([disabled="true"]):not([level]), menulist:not([disabled="true"]) {
  color: -moz-fieldtext !important;
}
#urlbar :not(dropmarker):not(.progress-bar), searchbar button {
  -moz-border-radius: 14pt !important;
}
menulist dropmarker {
  display: -moz-box !important;
}
menulist dropmarker *, .autocomplete-history-dropmarker * {
  display: none !important;
}
menulist dropmarker {
  margin-top: 1.8pt !important;
}
richlistbox menulist dropmarker {
  -moz-appearance: menulist-button !important;
  margin-top: -2.5pt !important;
  margin-bottom: -2.5pt !important;
  margin-right: -1pt !important;
}
toolbar splitter {
  outline: highlight 1pt solid !important;
  -moz-outline-radius: 12121212px !important;
  outline-offset: -10pt !important;
  height: 20pt !important;
  width: 24pt !important;
  border: none !important;
  padding: 0 !important;
  margin-left: -9pt !important;
  margin-right: -6.5pt !important;
}
#identity-box {
  padding: 0 !important;
  padding-right: 0.1pt !important;
  -moz-background-clip: border !important;
  margin-top: 0 !important;
  margin-bottom: 0 !important;
  margin-left: -1pt !important;
  border: none !important;
}
#identity-box>hbox {
  margin: -1px !important;
  min-width: 18px !important;
  border: none !important;
  min-height: 15px !important;
  background: -moz-field !important;
  padding-top: 0 !important;
  padding-bottom: 0 !important;
  padding-left: 1.5pt !important;
  padding-right: 1pt !important;
  margin: 0 !important;
}
#urlbar :not(dropmarker), searchbar * {
  border: none !important;
}
#identity-box.verifiedIdentity, #identity-box.verifiedDomain {
  background: rgba(0, 0, 0, 0.5) !important;
}
#identity-box.verifiedIdentity>hbox {
  background: rgba(200, 255, 200, 0.9) !important;
}
#identity-box.verifiedDomain>hbox {
  background: rgba(190,190,255,0.9) !important;
}

#urlbar[level]:not([level="high"]),
#urlbar[level]:not([level="high"]) .autocomplete-textbox-container,
#urlbar[level]:not([level="high"]) .autocomplete-textbox-container * {
  background-color: rgb(253,196,196) !important;
  color: black !important;
}
#urlbar[level="high"],
#urlbar[level="high"] .autocomplete-textbox-container,
#urlbar[level="high"] .autocomplete-textbox-container * {
/*  background-color: rgb(192,247,192) !important;*/
/*  background-color: rgb(253,253,196) !important;*/
/*  color: black !important;*/
}
#urlbar[level="high"] {
  background: -moz-Field !important;
}

#identity-box.verifiedDomain label {
  /*display: -moz-box !important;*/
}
#identity-box label {
  margin-right: 3.1pt !important;
  color: black !important;
}
menulist dropmarker, textbox dropmarker {
  width: 0px !important;
  border-top: 6.5pt solid highlight !important;
  border-left: 4pt solid rgba(0, 0, 0, 0) !important;
  border-right: 4pt solid rgba(0, 0, 0, 0) !important;
  border-bottom: none !important;
  -moz-border-top-colors: highlight !important;
  -moz-border-left-colors: rgba(0, 0, 0, 0) !important;
  -moz-border-right-colors: rgba(0, 0, 0, 0) !important;
  -moz-border-bottom-colors: rgba(0, 0, 0, 0) !important;
  background: none !important;
  margin-top: 4pt !important;
  margin-right: 3pt !important;
  margin-left: 1.6pt !important;
  -moz-border-radius-bottomright: 12pt !important;
}
#searchbox textbox {
  border: none !important;
  outline-offset: 4px !important;
  margin-right: -15px !important;
  padding-right: 17px !important;
}
spinbuttons, spinbuttons * {
  -moz-appearance: none !important;
  border: none !important;
  padding: 0 !important;
  margin-top: -0.5pt !important;
  margin-bottom: -0.5pt !important;
  background-color: rgba(0, 0, 0, 0) !important;
}
.textbox-input-box.numberbox-input-box {
  -moz-appearance: none !important;
  border: none !important;
}
.find-field-container {
  -moz-appearance: none !important;
  border: none !important;
  background: none !important;
}
.findbar-container {
  -moz-appearance: toolbox !important;
  margin-top: 1px !important;
}
findbar {
  -moz-appearance: toolbar !important;
  margin-bottom: -1px !important;
}
#urlbar .progress-bar {
  -moz-border-radius: 9.5pt !important;
  background: rgba(0,0,255,0.2) !important;
  margin-top: -1px !important;
  margin-bottom: -1px !important;
}
/* For some weird reason these don't work. */
#urlbar .verifiedIdentity+stack>progressmeter>.progress-bar {
  background: rgba(200, 255, 200, 0.9) !important;
}
#urlbar .verifiedDomain+stack>progressmeter>.progress-bar {
  background: rgba(200, 210, 255, 0.99) !important;
}

.gtb-search-box {
  -moz-appearance: none !important;
  background: none !important;
  border: none !important;
}
.gtb-search-box dropmarker {
  display: none !important;
}



	
/*   ======================================================BEGIN======================================================   */  

/* Hide urlbar and searchbar drop-down arrows */
	#urlbar .autocomplete-history-dropmarker
	  	{ display: none !important; } 
		
	#searchbar .autocomplete-history-dropmarker 
	   	{ display: none !important; }

/* Fix position and margins of searchbar */
	#searchbar
		{ min-height: 28px !important;
        	max-height: 28px !important;
		margin: 0 0 0 0 !important; }   

/* Hide search engines button from searchbar*/
       .searchbar-dropmarker#searchbar-dropmarker  
	        { display: none !important; }
       .searchbar-engine-button-container  
	        { display: none !important; }
       .searchbar-engine-button  
		{ display: none !important; } 

/*  Hide Search Engine Name in searchbar  */ 
        textbox[empty="true"] .textbox-input-box 
        	{ color: #323232 !important; } 

/*  Urlbar text left margin  */
        #urlbar .textbox-input-box  
		{ margin-left: 5px !important; }
		
/*  Searchbar text left margin  */
        #searchbar .textbox-input-box 
		{ margin-left: 5px !important; } 		
		
/*  Old style go button without star  */  
        #star-button  
		{ display: none !important; } 
        #go-button  
		{ visibility: visible !important; }

/*  Hide RSS icon from location bar  */        
        #feed-button 
		{ display: none !important }

/* Group reload and stop buttons (user must place stop button on the left of reload on toolbar)*/
        #stop-button[disabled="true"]
		{ display:none; } 
        #stop-button:not([disabled]) + #reload-button 
		{ display:none; }	

/*  Hide Forward Back Dropmaker  */      
        #back-forward-dropmarker 
        	{ display:none; } 		
		
		
		
/*   ======================================================CONTEXT====================================================   */            
 
 

/*  Remove Items In Context Menu   */ 
        #context-back, /* "Back" */
	#context-forward, /* "Forward" */
	#context-reload, /* "Reload" */
        #context-stop, /* "Stop" */
	#context-bookmarkpage, /* "Bookmark This Page..." */
	#context-savepage, /* "Save Page As..." */
	#context-sendpage, /* "Send Link..." (showed on webpage) */
	#context-viewbgimage, /* "View Background Image" */

/*  Remove Items In Context Menu: LINKS  */
	#context-bookmarklink, /* "Bookmark This Link..." */
	#context-sendlink, /* "Send Link..." (showed on links) */

/*  Remove Items In Context Menu: IMAGES  */
	#context-viewimage, /* "View Image" */
	#context-copyimage-contents, /* "Copy Image" */
	#context-back, /* "Back" */
	#context-forward, /* "Forward" */
	#context-reload, /* "Reload" */
	#context-stop, /* "Stop" */
	#context-bookmarkpage, /* "Bookmark This Page..." */
	#context-savepage, /* "Save Page As..." */
	#context-sendpage, /* "Send Link..." (showed on webpage) */
	#context-viewbgimage, /* "View Background Image" */
	#context-copyimage, /* "Copy Image Location" */
	#context-sendimage, /* "Send Image..." */
	#context-setWallpaper, /* "Set As Wallpaper..." */
	#context-setDesktopBackground, /* "Set As Desktop Background..." */

/*  Remove Items In Context Menu: LINKS  */
		/*  #context-openlinkintab, /* "Open Link in New Tab" */
	#context-bookmarklink, /* "Bookmark This Link..." */
	#context-sendlink, /* "Send Link..." (showed on links) */
	#context-copyemail, /* "Copy Email Address" */

/*  Remove Items In Context Menu: TEXT  */
        #context-selectall, /* "Select All" */
	#context-viewpartialsource-selection, /* "View Selection Source" */

/*  Remove Items In Context Menu: EXTRA  */
	#context-printpage, /* "Print..." */
	#frame, /* "This Frame" */
	#context-viewsource, /* "View Page Source" */
	#context-viewinfo, /* "View Page Info" */
	#context-metadata, /* "Properties" */
	#context-keywordfield, /* "Add a Keyword for this Search" */
	#formfillerDebugPanel, /* "formfiller statusbar debug of debug" */

		
		
/*   ==========================================================MENU===================================================   */  	  



/*  File  */
	menuitem[command="cmd_newNavigatorTab"],  /* New Window */
	menuitem[command="Browser:OpenLocation"],  /* Open Location */
	#menu_closeWindow,  /*  */
        #menu_close,  /*  */
        #menu_sendLink,  /*  */
        #goOfflineMenuitem,  /*  */
        menuitem[command="cmd_pageSetup"],  /* Page Setup... */
        menuitem[command="cmd_printPreview"],  /* Print Preview */
        menuitem[command="cmd_print"],  /* Print... */
        menuitem[oncommand^="BrowserImport();"],  /* Import... */
        menuitem[command="cmd_quitApplication"],  /* Quit */
        
/*  Edit  */
	/*	#edit-menu, */
        menuitem[command="cmd_undo"],  /* Undo */
        menuitem[command="cmd_redo"],  /* Redo */
        menuitem[command="cmd_cut"],  /* Cut */
        /*  menuitem[command="cmd_copy"],     Copy */
        /*  menuitem[command="cmd_paste"],     Paste */ 
        /*  menuitem[command="cmd_delete"],     Delete */
        menuitem[command="cmd_selectAll"],  /* Select All */
        menuitem[command="cmd_find"],  /* Find */
        menuitem[command="cmd_findAgain"],  /* Find Again */

/*  View  */
	#viewToolbarsMenu,  /* Toolbars */
	menuitem[command="Browser:Stop"],  /* Stop */
	menuitem[command="Browser:Reload"],  /* Reload */
        menuitem[command="View:FullScreen"],  /* Full Screen */
        
/*  History  */
	menuitem[oncommand^="BrowserBack(event, true)"],  /* Back */
	menuitem[oncommand^="BrowserForward(event, true)"],  /* Forward */
	menuitem[oncommand^="BrowserGoHome(event);"],  /* Home */
        #historyUndoMenu,  /* Recently Closed Tabs */

/* Bookmarks  */
	menuitem[command="Browser:AddBookmarkAs"],  /*  */
	menuitem[command="Browser:BookmarkAllTabs"],  /*  */
	menuitem[label="Get Bookmark Add-ons"],  /*  */
	#subscribeToPageMenuitem,  /*  */
        #bookmarksToolbarFolderMenu,   /*  */

/*  Tools  */
	menuitem[command="Tools:Search"],  /*  */
	#tabmix-menu,   /*  */
        #tm-sm-closedwindows,   /*  */
       /* #tm-sm-settings,     */
        #tm-sm-closedwindows2,   /*  */
        #tm-sm-saveone,   /*  */
        #tm-sm-saveall,   /*  */
        #flashgot-menu,  /*  */
        #abp-menuitem,   /*  */
        
/*  Help  */
       /* menuitem[oncommand^="openHelpLink('ieusers');"],   For Internet Explorer Users */
	#menu_HelpPopup_reportertoolmenu,  /*  */
	#menu_HelpPopup_reportPhishingtoolmenu,  /*  */
        menuitem[oncommand^="openReleaseNotes(event)"],  /* Release Notes */
        menuitem[oncommand^="openHelpLink('firefox-help')"]    /* Help Contents */
               { display: none !important; }
      
	  
	  
/*   ========================================================TABS=====================================================   */  


	   
/*  First tab left margin  */
        .tabbrowser-tab[first-tab="true"]
        	{ margin-left: 1px !important; } 

/*  Show first tab without padding on the left  */  
        .tabs-container:not([overflow="true"]) 
        	{ -moz-padding-start: 0px !important; }

/*  Distance between all tabs  */
        .tabbrowser-tabs .tabbrowser-tab 
        	{ margin-right: 1px !important; }
		
/*  Hide focus rings around active tab  */
        .tabbrowser-tabs > tab:focus .tab-middle
        	{-moz-outline: none !important; }  
        .tab-text
        	{ border: none !important; }   
        .tabbrowser-tab[selected="true"]:focus
        	{ -moz-border-top-colors: #000000 #DFE2E6 #D0D7DD !important;
        	-moz-border-right-colors: #000000 #BAC2CD #C1C9D3 !important;
        	-moz-border-bottom-colors: #C7D0D9 !important;
        	-moz-border-left-colors: #000000 #DFE2E6 #D0D7DD !important; }
        
/*  Static throbber on Bars  */
	#navigator-throbber 
		{ list-style-image: url("throbber-16.gif") !important; }

/*  Animated throbber on Bars  */
	#navigator-throbber[busy="true"] 
		{ list-style-image: url("throbber-16-anim.gif") !important; }

/*  Animated throbber on Tabs  */
	#main-window[firefox3] .tabbrowser-tab[busy]
		 > hbox.tab-image-middle > .tab-icon > .tab-icon-image
		{ list-style-image: url("throbber-16-anim.gif") !important;
		opacity: 1.0 !important; }

	#main-window[firefox3] .alltabs-item[busy] > .menu-iconic-left > .menu-iconic-icon
		{ list-style-image: url("throbber-16-anim.gif") !important;
		-moz-image-region: rect(0px 16px 16px 0px) !important;
		opacity: 1.0 !important; }

	#main-window[firefox3] .alltabs-item[busy][_moz-menuactive="true"]
	> .menu-iconic-left > .menu-iconic-icon
		{ -moz-image-region: rect(0px 32px 16px 16px) !important; }  


/*   =====================================================OTHER=======================================================   */  
 
 

/*  Use the old-style QuickFind Bar */
        .findbar-container > *
		{ display: -moz-box; }

/* Remove bookmark toolbar folder arrows */
       #PersonalToolbar .toolbarbutton-menu-dropmarker 
       		{display: none !important;} 

/* Hide bookmarks context menuitems */ 
        menuitem[label="New Separator"],
        menuitem[label="Sort By Name"],
        menuitem[label="Open in a New Tab"],
        menuitem[label="Open All in Tabs"],
        menuitem[label="Open"],
        menuitem[command="placesCmd_new:bookmark"] 
                { display: none !important; } 
			   
/*  Hide menu separators  */
        menuseparator 
		{ display: none; }  

/*  Hide disabled menuitems  */      
        menuitem[disabled="true"],
        menuitem[disabled="true"] + menuseparator
                { display: none; }	

/* Hide hotkeys from menus */   	 	
	.menu-iconic-accel 
		{ display: none !important; }
        .menu-accel 
		{ display: none !important; }	

/* Precise position of toolbar elements */
	#toolbar-menubar 
		{ margin-right: 5px !important; 
		margin-left: -6px !important; 
		padding-bottom: 2px !important; }

        #back-button 
		{ margin-left: -9px !important; }

	#navigator-throbber 
		{ margin-left: 4px !important; }
	

/* Fix height of personal toolbar */
	#PersonalToolbar
		{ height: 28px !important; }

	#bookmarksBarContent
		{ margin-top: -4px !important;
		margin-bottom: -4px !important; }

/* Hide zero between urlbar and searchbar */
	#urlbar-search-splitter
		{ display: none !important; }

/* Fix vertical text position in urlbar and searchbar */
	.textbox-input-box 
		{ margin-top: 2px !important; }

/* Fix back button vertical position */
	#back-button
		{ margin-top: 2px !important; }



/*   ======================================================END========================================================   */  
```

---

