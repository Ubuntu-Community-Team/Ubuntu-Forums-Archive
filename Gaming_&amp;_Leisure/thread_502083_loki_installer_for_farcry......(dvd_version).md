---
title: "loki installer for farcry......(dvd version)"
date: 2007-07-16
forum: Gaming &amp; Leisure
---

### Post by techno-mole on 2007-07-16
hello, ive been trying to install farcry with cedega, which according to cedega they support it, but i dont think it is supported at all, basically it wont install with cedega, so ive done some looking and from what ive read most people have had the same problem and have said the best way to install it is with a loki installer (thats what most people on the cedega forums have done) 
i find it odd that people have had to use a loki installer because cedega doesnt work, and you have to pay for it !
anyway i cant find the loki installer anywhere, maybe because its an old game.
so i thought id ask to see if anybody has it saved in a folder on a hard drive somewhere, and if they do could it be e-mailed to me ?
cheers.
ive tried wine aswell but it would have it either.

---

### Post by cogadh on 2007-07-16
Loki removed all of its installers for Wine playable games because, according to the Loki site, all of those games can already be installed correctly through Wine. I found out that is not entirely true when I tried to install Call of Duty normally and it failed miserably.

That being said, Wine's AppDB confirms that Far Cry is able to be installed normally through Wine and runs quite well. What version of Wine are you using and how are you trying to install the game (i.e. what command are you running in the terminal)? Also, what error messages are produced in the terminal when you try to install the game?

---

### Post by techno-mole on 2007-07-16
im currently running wine 0.9.33.
thats the problem, i dont get any errors, for example if i try to install it with cedega ill get the first window that says - choose setup language, i select english and click ok, then the install shield window pops up and it'll get as far as configuring the installer then the window disappears, ive tried various settings and get the same result every time.
i did try it with wine and it actually went through the whole install process with no errors and didnt actually install anything, i checked every wine folder and wine related folder and nothing.
to install it with wine i open terminal and type wine and then the link to were the .exe is so it looks something like this -  wine '/media/dvdrw/setup.exe'  and like i said it will go through the whole setup process with no errors, but it doesnt install anything.
cheers.
ive just run it again with wine, and i would post the output but i get a message about images (even though i havent put any in the post) im guessing its because the output im trying to post is too big.

---

### Post by cogadh on 2007-07-16
This may be a silly question, but when you say you checked every Wine folder for the installed files, did you look in the hidden ".wine" folder in your home directory?

Also, it may be worth it to update to the latest version of Wine (0.9.41), it includes numerous bugfixes. Just follow the instructions [here]("http://www.winehq.org/site/download-deb") to install it.

When you post text from the terminal, try using the forum [code] tags, that may allow you to get the info into the post correctly.

---

### Post by techno-mole on 2007-07-16
1. You have included 54 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again.

      Images include use of smilies, the vB code [img] tag and HTML <img> tags. The use of these is all subject to them being enabled by the administrator.

this is the error i got trying to post the terminal output from wine, i used the [code] tags but no dice.
i have updated wine to the latest version, and i have managed to get farcry to install, but it wont run, so im presuming somethings wrong with my installation of wine, surely it shouldnt give of any errors ?
like i said i would post the output from terminal but i cant, i dont know why it says ive included images when i havent, but there you go.
cheers

---

### Post by cogadh on 2007-07-16
The output from the terminal will often include accidental instances of smiley text, but if you place the {code} and {/code} tags around it (change the { } to [ ] ), that problem should go away. Its really odd that the forum is erroring on that.

Just because the game installed fine, doesn't mean it won't produce errors when run. Also, just because AppDB says the game runs, also doesn't mean it won't run with errors. Wine is constantly in debug mode, so error messages are constantly produced when it is used. Most of those messages can be ignored, as they only apply to the developers and have no meaning to users (for example, the numerous "fixme" messages). The rest of the messages may be important (the "err" and "Warning" messages).

Try doing this in the terminal to run the game:
```
cd $HOME/.wine/drive_c/Program Files/Ubisoft/Crytek/Far Cry
wine /Bin32/FarCry.exe
```
That will put the terminal into the game's install directory when it is run. If you don't do that, most games will  error out, saying they can't find the installed files. If that works, we can create a shortcut that will do the same thing for you and will make launching the game a lot less cumbersome.

EDIT -  One other *minor* point I kind of forgot. Wine will sometimes fail without any errors when it encounters problems with copy protection software. You may need to download and use a cracked .exe to run the game properly. In fact, I just checked the AppDB entry again and it does say the game will only run if you use a cracked .exe.

---

### Post by techno-mole on 2007-07-16
well, i managed to get the configuration editor to load (if i remember it starts then the game loads under windows) but thats it, im trying it with a cracked .exe aswell but no dice, cheers for the help though.
i think more companies should port stuff to linux in the way of games, to be honest i think that maybe the one thing that keeps alot of users from fully switching to linux based os's.
on another note i am having problems with my dvd drive at the moment, nothing to do with ubuntu, its old and i have used it to the point of abuse with dvd burning, it'll be the second one ive worn out.
cheers again, i shall have to do more reading up on wine and games.
```

fixme:dxdiag:DXDiag_AddFileDescContainer (0x969398,L"dmloader.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"szPath", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"szName", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"bExists", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"szVersion", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"szAttributes", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"szLanguageEnglish", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"dwFileTimeHigh", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"dwFileTimeLow", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"bBeta", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"bDebug", 0x340ebc)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x969398,L"dmscript.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"szPath", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"szName", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"bExists", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"szVersion", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"szAttributes", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"szLanguageEnglish", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"dwFileTimeHigh", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"dwFileTimeLow", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"bBeta", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"bDebug", 0x340ebc)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x969398,L"dmstyle.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"szPath", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"szName", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"bExists", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"szVersion", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"szAttributes", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"szLanguageEnglish", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"dwFileTimeHigh", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"dwFileTimeLow", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"bBeta", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"bDebug", 0x340ebc)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x969398,L"dmsynth.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"szPath", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"szName", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"bExists", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"szVersion", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"szAttributes", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"szLanguageEnglish", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"dwFileTimeHigh", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"dwFileTimeLow", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"bBeta", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"bDebug", 0x340ebc)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x969398,L"dmusic.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"szPath", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"szName", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"bExists", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"szVersion", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"szAttributes", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"szLanguageEnglish", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"dwFileTimeHigh", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"dwFileTimeLow", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"bBeta", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"bDebug", 0x340ebc)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x969398,L"devenum.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"szPath", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"szName", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"bExists", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"szVersion", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"szAttributes", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"szLanguageEnglish", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"dwFileTimeHigh", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"dwFileTimeLow", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"bBeta", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"bDebug", 0x340ebc)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x969398,L"quartz.dll")
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"szPath", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"szName", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"bExists", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"szVersion", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"szAttributes", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"szLanguageEnglish", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"dwFileTimeHigh", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"dwFileTimeLow", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"bBeta", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x969398, L"bDebug", 0x340ebc)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x968c08, L"DxDiag_DirectXFiles", 0x969398)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x96d760, L"0", 0x96d780)
fixme:win:EnumDisplayDevicesW ((null),0,0x340f40,0x00000000), stub!
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x96d780, L"szDeviceName", 0x34163c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x96d780, L"szDescription", 0x34162c)
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x24f0020) : stub, simulating 64MB for now, returning 64MB left
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x96d780, L"szDisplayMemoryLocalized", 0x34165c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x96d780, L"szDisplayMemoryEnglish", 0x34164c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x96d780, L"dwWidth", 0x34161c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x96d780, L"dwHeight", 0x34160c)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x96d780, L"dwBpp", 0x3415fc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x96d780, L"szVendorId", 0x3415ec)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x96d780, L"szDeviceId", 0x3415dc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x96d780, L"szKeyDeviceKey", 0x3415cc)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x96d780, L"szKeyDeviceID", 0x3415bc)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x96dec0)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x968c08, L"DxDiag_DisplayDevices", 0x96d760)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x96d920, L"DxDiag_SoundDevices", 0x96def8)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x96d920, L"DxDiag_SoundCaptureDevices", 0x96df60)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x968c08, L"DxDiag_DirectSound", 0x96d920)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x968c08, L"DxDiag_DirectMusic", 0x96e020)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x968c08, L"DxDiag_DirectInput", 0x96e088)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x968c08, L"DxDiag_DirectPlay", 0x96e0f0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({083863f1-70de-11d0-bd40-00a0c911ce86}) pEnum(0x24f0170)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x24f0170, 1, 0x24f0188)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szCatName", 0x340e94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szClsidCat", 0x340e94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szName", 0x340e94)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"AVI Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{1B544C20-FD0B-11CE-8C63-00AA0044B51E}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szClsidFilter", 0x340e94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szName", 0x340e84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"dwMerit", 0x340e84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"dwInputs", 0x340e84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"dwOutputs", 0x340e84)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x24f0170, 1, 0x24f0390)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szCatName", 0x340e94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szClsidCat", 0x340e94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szName", 0x340e94)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"MPEG-I Stream Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{336475D0-942A-11CE-A870-00AA002FEAB5}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szClsidFilter", 0x340e94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szName", 0x340e84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"dwMerit", 0x340e84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"dwInputs", 0x340e84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"dwOutputs", 0x340e84)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x24f0170, 1, 0x24f0808)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szCatName", 0x340e94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szClsidCat", 0x340e94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szName", 0x340e94)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"ACM Wrapper"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{6A08CF80-0E18-11CF-A24D-0020AFD79767}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szClsidFilter", 0x340e94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szName", 0x340e84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"dwMerit", 0x340e84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"dwInputs", 0x340e84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"dwOutputs", 0x340e84)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x24f0170, 1, 0x24f0bf8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szCatName", 0x340e94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szClsidCat", 0x340e94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szName", 0x340e94)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{70E102B0-5556-11CE-97C0-00AA0055595A}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szClsidFilter", 0x340e94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szName", 0x340e84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"dwMerit", 0x340e84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"dwInputs", 0x340e84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"dwOutputs", 0x340e84)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x24f0170, 1, 0x24f11e0)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szCatName", 0x340e94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szClsidCat", 0x340e94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szName", 0x340e94)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"AVI Decompressor"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{CF49D4E0-1115-11CE-B03A-0020AF0BA770}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szClsidFilter", 0x340e94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szName", 0x340e84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"dwMerit", 0x340e84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"dwInputs", 0x340e84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"dwOutputs", 0x340e84)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x24f0170, 1, 0x24f1608)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szCatName", 0x340e94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szClsidCat", 0x340e94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szName", 0x340e94)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Wave Parser"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{D51BD5A1-7548-11CF-A520-0080C77EF58A}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szClsidFilter", 0x340e94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szName", 0x340e84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"dwMerit", 0x340e84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"dwInputs", 0x340e84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"dwOutputs", 0x340e84)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x24f0170, 1, 0x24f1a60)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szCatName", 0x340e94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szClsidCat", 0x340e94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szName", 0x340e94)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"File Source (Async.)"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E436EBB5-524F-11CE-9F53-0020AF0BA770}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szClsidFilter", 0x340e94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szName", 0x340e84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"dwMerit", 0x340e84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"dwInputs", 0x340e84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"dwOutputs", 0x340e84)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a760-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x24f0148)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a761-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x24f0148)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a762-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x24f2388)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x24f2388, 1, 0x24f2438)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szCatName", 0x340e94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szClsidCat", 0x340e94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szName", 0x340e94)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"mixer00"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E30629D2-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szClsidFilter", 0x340e94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szName", 0x340e84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"dwMerit", 0x340e84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"dwInputs", 0x340e84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"dwOutputs", 0x340e84)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({4efe2452-168a-11d1-bc76-00c04fb9453b}) pEnum(0x24f0100)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x24f0100, 1, 0x24f0118)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szCatName", 0x340e94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szClsidCat", 0x340e94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szName", 0x340e94)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"CA0106 MPU-401 (UART)"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{07B65360-C445-11CE-AFDE-00AA006C14F4}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szClsidFilter", 0x340e94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szName", 0x340e84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"dwMerit", 0x340e84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"dwInputs", 0x340e84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"dwOutputs", 0x340e84)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x24f0100, 1, 0x24f0130)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szCatName", 0x340e94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szClsidCat", 0x340e94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szName", 0x340e94)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Midi Through Port-0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{07B65360-C445-11CE-AFDE-00AA006C14F4}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szClsidFilter", 0x340e94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szName", 0x340e84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"dwMerit", 0x340e84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"dwInputs", 0x340e84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"dwOutputs", 0x340e84)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({860bb310-5d01-11d0-bd3b-00a0c911ce86}) pEnum(0x24f1e30)
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({cc7bfb41-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({cc7bfb46-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({e0f158e1-cb04-11d0-bd4e-00a0c911ce86}) pEnum(0x24f2388)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x24f2388, 1, 0x24f35b0)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szCatName", 0x340e94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szClsidCat", 0x340e94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szName", 0x340e94)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"DirectSound: mixer00"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szClsidFilter", 0x340e94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szName", 0x340e84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"dwMerit", 0x340e84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"dwInputs", 0x340e84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"dwOutputs", 0x340e84)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x24f2388, 1, 0x24f35c8)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szCatName", 0x340e94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szClsidCat", 0x340e94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szName", 0x340e94)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"mixer00"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E30629D1-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szClsidFilter", 0x340e94)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"szName", 0x340e84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"dwMerit", 0x340e84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"dwInputs", 0x340e84)
fixme:dxdiag:IDxDiagContainerImpl_AddProp (0x24f0050, L"dwOutputs", 0x340e84)
fixme:dxdiag:IDxDiagContainerImpl_AddChildContainer (0x968c08, L"DxDiag_DirectShowFilters", 0x24f0050)
fixme:dxdiag:IDxDiagContainerImpl_GetChildContainer (0x968c08, L"DxDiag_SystemInfo", 0x3416f0)
fixme:dxdiag:IDxDiagContainerImpl_GetProp (0x968c28, L"dwDirectXVersionMajor", 0x3416fc)
fixme:dxdiag:IDxDiagContainerImpl_GetProp (0x968c28, L"dwDirectXVersionMinor", 0x3416fc)
fixme:dxdiag:IDxDiagContainerImpl_GetProp (0x968c28, L"szDirectXVersionLetter", 0x3416fc)
fixme:advapi:LookupAccountNameW (null) L"danny" (nil) 0x7bda4078 (nil) 0x7bda407c 0x7bda4070 - stub
fixme:advapi:LookupAccountNameW (null) L"danny" 0x25a6918 0x7bda4078 0x25a5700 0x7bda407c 0x7bda4070 - stub
fixme:rpc:RpcMgmtWaitServerListen not waiting for server calls to finish
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:rpc:RpcImpersonateClient (0x279cd00): stub
fixme:rpc:RpcRevertToSelfEx (0x279cd00): stub
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:rpc:RpcImpersonateClient (0x279d438): stub
fixme:rpc:RpcRevertToSelfEx (0x279d438): stub
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:rpc:RpcImpersonateClient (0x279cf18): stub
fixme:rpc:RpcRevertToSelfEx (0x279cf18): stub
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:rpc:RpcImpersonateClient (0x279d8b8): stub
fixme:rpc:RpcRevertToSelfEx (0x279d8b8): stub
fixme:msi:msi_unimplemented_action_stub UnpublishFeatures -> 373 ignored L"FeatureComponents" table values
fixme:msi:msi_unimplemented_action_stub RemoveShortcuts -> 9 ignored L"Shortcut" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 218 ignored L"CreateFolder" table values
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:rpc:RpcImpersonateClient (0x29c1d78): stub
fixme:rpc:RpcRevertToSelfEx (0x29c1d78): stub
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:msi:MsiGetMode 4 6
fixme:rpc:RpcImpersonateClient (0x2180f0): stub
fixme:rpc:RpcRevertToSelfEx (0x2180f0): stub
fixme:rpc:RpcImpersonateClient (0x217558): stub
fixme:rpc:RpcRevertToSelfEx (0x217558): stub
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:rpc:RpcImpersonateClient (0x2a0d618): stub
fixme:rpc:RpcRevertToSelfEx (0x2a0d618): stub
fixme:msi:ACTION_CustomAction msidbCustomActionTypeNoImpersonate not handled
fixme:rpc:RpcImpersonateClient (0x2a0d978): stub
fixme:rpc:RpcRevertToSelfEx (0x2a0d978): stub
fixme:shell:DllCanUnloadNow stub
fixme:advapi:LookupAccountNameW (null) L"danny" (nil) 0x34d088 (nil) 0x34d08c 0x34d080 - stub
fixme:advapi:LookupAccountNameW (null) L"danny" 0x25fbaf0 0x34d088 0x25fb638 0x34d08c 0x34d080 - stub
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
err:ole:marshal_object object doesn't expose interface {60e73571-8258-478b-bd66-a7c07319cc89}, failing with error 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x257f958)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
fixme:ntdll:NtQuerySecurityObject (0x13c,0x00000004,(nil),0x00000000,0x34e080) stub!
fixme:ntdll:NtQuerySecurityObject (0x13c,0x00000004,0x5b3720,0x0000005c,0x34e080) stub!
fixme:advapi:SetFileSecurityW (L"c:\\Program Files\\InstallShield Installation Information\\{D6DBDC2A-E72C-4284-B6AD-6B3B61B4DABC}\\Setup.ilg") : stub

```
this is the output from terminal.
cheers again.

---

