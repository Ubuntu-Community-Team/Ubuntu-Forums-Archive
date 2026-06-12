---
title: "Sancho not works"
date: 2007-08-14
forum: Desktop Environments
---

### Post by msx2 on 2007-08-14
Hi everybody!

When i try run the sancho these errors leave:

```
Unhandled Java exception:
org.eclipse.swt.SWTException: Unsupported or unrecognized format
   at org.eclipse.swt.SWT.error(sancho)
   at org.eclipse.swt.SWT.error(sancho)
   at org.eclipse.swt.SWT.error(sancho)
   at org.eclipse.swt.internal.image.FileFormat.load(sancho)
   at org.eclipse.swt.graphics.ImageLoader.load(sancho)
   at org.eclipse.swt.graphics.ImageDataLoader.load(sancho)
   at org.eclipse.swt.graphics.ImageData.<init>(sancho)
   at org.eclipse.jface.resource.FileImageDescriptor.getImageData(sancho)
   at org.eclipse.jface.resource.ImageDescriptor.createImage(sancho)
   at org.eclipse.jface.resource.ImageDescriptor.createResource(sancho)
   at org.eclipse.jface.resource.DeviceResourceManager.allocate(sancho)
   at org.eclipse.jface.resource.AbstractResourceManager.create(sancho)
   at org.eclipse.jface.resource.ResourceManager.createImageWithDefault(sancho)
   at org.eclipse.jface.resource.ImageRegistry.get(sancho)
   at org.eclipse.jface.resource.JFaceResources.getImage(sancho)
   at org.eclipse.jface.dialogs.TitleAreaDialog.createTitleArea(sancho)
   at org.eclipse.jface.dialogs.TitleAreaDialog.createContents(sancho)
   at org.eclipse.jface.wizard.WizardDialog.createContents(sancho)
   at org.eclipse.jface.window.Window.create(sancho)
   at org.eclipse.jface.dialogs.Dialog.create(sancho)
   at sancho.core.CoreFactory$4.run(sancho)
   at org.eclipse.swt.widgets.Synchronizer.syncExec(sancho)
   at org.eclipse.swt.widgets.Display.syncExec(sancho)
   at sancho.core.CoreFactory.setupWizard(sancho)
   at sancho.core.CoreFactory.checkIfInitialized(sancho)
   at sancho.core.CoreFactory.interactiveConnect(sancho)
   at sancho.core.Sancho.interactiveLaunch(sancho)
   at sancho.core.Sancho.main(sancho)
```

Somebody can helpme?

Thanks,

---

