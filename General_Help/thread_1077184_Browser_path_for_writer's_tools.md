---
title: "Browser path for writer's tools???"
date: 2009-02-22
forum: General Help
---

### Post by phatjonny on 2009-02-22
have installed OO 3.0 and writer's tools but made a mess of adding the browser path.  

When I try using the features this is what I get.  I really appreciate the help.

John

Sub BrowseURL(URLString as String)
	
	Select Case GetGuiType()
	' Windows
	Case 1
		Dim SplitString1() as String
		Dim SplitString2() as String
		Dim JointString1 as String
		Dim FinalURLString as String
		
		SplitString1 = Split(URLString, "&")
		FinalURLString = Join(SplitString1, """&""")
		
		ReadBrowserPath()
		Shell(DefaultBrowser, 1, FinalURLString)
		
	' Mac OS
	Case 3
		ReadBrowserPath()
		Shell(DefaultBrowser, 1, URLString)
		
	' Unix
	Case 4
		ReadBrowserPath()
		home/john/openoffice3.0/john
		
	
		'Shell(DefaultLinuxBrowser, 1, URLString)
	End Select
	Exit Sub
	
End Sub

'************************************************************
'	VISUAL WORD COUNT
'************************************************************

Sub VisualWordCount()

ThisDoc=ThisComponent
CurrentCount=ThisDoc.WordCount

TargetCount=InputBox(InputTargetWordCount, InputWordCount)

If TargetCount="" Then End

OpenDialog("WordCountDialog")
Dialog=CreateUnoDialog(TheDialog)

NumericField1=Dialog.GetControl("NumericField1").setValue(CurrentCount)

Value=Int((CurrentCount/TargetCount)*100)

Bar=Dialog.GetControl("ProgressBar1")
Bar.Value=Value

NumericField2=Dialog.getControl("NumericField2").setValue(Value)

Dialog.Execute

End Sub

---

### Post by phatjonny on 2009-02-22
So I have tried uninstalling writer's tool and trying again, but to no avail.

[http://code.google.com/p/writertools/wiki/FAQ](http://code.google.com/p/writertools/wiki/FAQ)  From here the advice is...

I entered incorrect browser path. How do I fix that?

On Windows with OpenOffice.org 3.0 Navigate to C:\Documents and Settings\USER\Application Data\OpenOffice.org\3\user (replace USER with your actual user name) and delete the writertools folder. In Windows Vista the path is C:\Users\USER\AppData\Roaming\OpenOffice.org\3\user. Next time you use Writer's Tools, you'll be prompted to enter the path to a browser.

On Linux with OpenOffice.org 3.0 Navigate to the hidden OpenOffice.org folder in your home directory and delete the writertools folder. Next time you use Writer's Tools, you'll be prompted to enter the path to a browser. 



But can somebody tell me what the path looks like, and where do I find it?  I know I don't need a map or a GPS, just a friendly pointer in the right direction:redface::redface:

---

### Post by phatjonny on 2009-02-24
bumptybump

---

