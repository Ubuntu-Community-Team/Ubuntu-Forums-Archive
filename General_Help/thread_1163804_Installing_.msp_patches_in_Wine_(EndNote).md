---
title: "Installing .msp patches in Wine (EndNote)"
date: 2009-05-19
forum: General Help
---

### Post by thenanodude on 2009-05-19
I am trying to install a .msp patch for Endnote v8.0  (patch downloaded from [http://www.endnote.com/support/EN802_Win_updater.asp](http://www.endnote.com/support/EN802_Win_updater.asp)).  from the terminal I run:

 $ wine msiexec /p /PATH/EN802Patch.msp

it pauses for about 2 seconds, then nothing happens at all.  With the debugging command:

 $ WINEDEBUG=trace+msiexec msiexec /p /PATH/EN802Patch.msp 

I get the following output:

> 
trace:msiexec:main argvW[1] = L"/p"
trace:msiexec:main argvW[2] = L"/PATH/EN802Patch.msp"
trace:msi:MsiSetInternalUI 00000005 (nil)
trace:msi:MsiApplyPatchW L"/PATH/EN802Patch.msp" (null) 0 (null)
trace:msi:MsiOpenDatabaseW L"/PATH/EN802Patch.msp" (null) 0x33fc98
trace:msi:MSI_OpenDatabaseW L"/PATH/EN802Patch.msp" (null)
trace:msidb:enum_stream_names stream  0 -> L"\4840\3f7f\4164\422f\4836" L"\4840_Tables"
trace:msidb:enum_stream_names stream  1 -> L"\4840\3f3f\4577\446c\3b6a\45e4\4824" L"\4840_StringData"
trace:msidb:enum_stream_names stream  2 -> L"\4840\3f3f\4577\446c\3e6a\44b2\482f" L"\4840_StringPool"
trace:msidb:enum_stream_names stream  3 -> L"\3b19\47e0\3a8c\47cb\394e\3941\39c4\390e" L"PCW_CAB_E51547E4"
trace:msidb:enum_stream_names stream  4 -> L"\0005DigitalSignature" L"\0005DigitalSignature"
trace:msidb:enum_stream_names stream  5 -> L"\0005SummaryInformation" L"\0005SummaryInformation"
trace:msidb:enum_stream_names stream  6 -> L"Target01ToUpgrade01" L"Target01ToUpgrade01"
trace:msidb:enum_stream_names stream  7 -> L"Target02ToUpgrade01" L"Target02ToUpgrade01"
trace:msidb:enum_stream_names stream  8 -> L"Target03ToUpgrade01" L"Target03ToUpgrade01"
trace:msidb:enum_stream_names stream  9 -> L"Target04ToUpgrade01" L"Target04ToUpgrade01"
trace:msidb:enum_stream_names stream 10 -> L"Target05ToUpgrade01" L"Target05ToUpgrade01"
trace:msidb:enum_stream_names stream 11 -> L"Target06ToUpgrade01" L"Target06ToUpgrade01"
trace:msidb:enum_stream_names stream 12 -> L"#Target01ToUpgrade01" L"#Target01ToUpgrade01"
trace:msidb:enum_stream_names stream 13 -> L"#Target02ToUpgrade01" L"#Target02ToUpgrade01"
trace:msidb:enum_stream_names stream 14 -> L"#Target03ToUpgrade01" L"#Target03ToUpgrade01"
trace:msidb:enum_stream_names stream 15 -> L"#Target04ToUpgrade01" L"#Target04ToUpgrade01"
trace:msidb:enum_stream_names stream 16 -> L"#Target05ToUpgrade01" L"#Target05ToUpgrade01"
trace:msidb:enum_stream_names stream 17 -> L"#Target06ToUpgrade01" L"#Target06ToUpgrade01"
trace:msidb:read_stream_data L"_StringPool" -> L"\4840\3f3f\4577\446c\3e6a\44b2\482f"
trace:msidb:read_stream_data L"_StringData" -> L"\4840\3f3f\4577\446c\3b6a\45e4\4824"
trace:msidb:msi_load_string_table Loaded 1 strings
trace:msi:alloc_msihandle 0x12d280 -> 1
trace:msi:MsiGetSummaryInformationW 1 (null) 0 0x33fc94
trace:msi:MSI_GetSummaryInformationW 0x12cc68 0
trace:msi:load_summary_info 0x12e568 0x12d488
trace:msi:alloc_msihandle 0x12e568 -> 2
trace:msi:MsiSummaryInfoGetPropertyW 2 7 0x33fc90 (nil) (nil) 0x7ee69766 0x33fc8c
trace:msi:get_prop 2 7 0x33fc90 (nil) (nil) 0x33fc34 0x33fc8c
trace:msi:MsiSummaryInfoGetPropertyW 2 7 0x33fc90 (nil) (nil) 0x12e6c8 0x33fc8c
trace:msi:get_prop 2 7 0x33fc90 (nil) (nil) 0x33fc34 0x33fc8c
trace:msi:MsiConfigureProductExW L"{27625A79-D272-41EF-844B-6EAC87D4A51E}" 0 5 L"PATCH=/PATH/EN802Patch.msp"
trace:msi:MsiSourceListGetInfoW L"{27625A79-D272-41EF-844B-6EAC87D4A51E}" L"LastUsedSource"
trace:msi:MSIREG_OpenUserProductsKey L"{27625A79-D272-41EF-844B-6EAC87D4A51E}"
trace:msi:MSIREG_OpenUserProductsKey squished (L"97A52672272DFE1448B4E6CA784D5AE1")
trace:msi:MsiSourceListGetInfoW L"{27625A79-D272-41EF-844B-6EAC87D4A51E}" L"PackageName"
trace:msi:MSIREG_OpenUserProductsKey L"{27625A79-D272-41EF-844B-6EAC87D4A51E}"
trace:msi:MSIREG_OpenUserProductsKey squished (L"97A52672272DFE1448B4E6CA784D5AE1")
trace:msi:MSI_OpenProductW L"{27625A79-D272-41EF-844B-6EAC87D4A51E}" 0x33fc38
trace:msi:MSIREG_OpenUninstallKey L"{27625A79-D272-41EF-844B-6EAC87D4A51E}"
trace:msi:MsiCloseHandle 2
trace:msi:MsiCloseHandle handle 2 destroyed
trace:msi:msiobj_release object 0x12e568 destroyed
trace:msi:MsiCloseHandle 1
trace:msi:MsiCloseHandle handle 1 destroyed
trace:msi:msiobj_release object 0x12d280 destroyed


Any help would be appreciated!

---

