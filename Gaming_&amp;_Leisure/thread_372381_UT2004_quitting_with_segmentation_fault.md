---
title: "UT2004 quitting with segmentation fault"
date: 2007-02-28
forum: Gaming &amp; Leisure
---

### Post by 351W on 2007-02-28
I'm running Dapper on an AMD Sempron 2000+ with an ATI Radeon 9550.
I've got the latest ATI drivers for the video card, and DRI is working.
Unreal Tournament 2004 installed flawlessly for me, but it quits randomly with a SIGSEGV (Segmentation Fault) error. I thought this was because of older video card drivers, but I upgraded to the most recent drivers from the ATI website, and now it actually seems to happen more often. I can post whatever logs you want to see, just name 'em.. thanks for any and all help.

Here are the last few lines of ~/.ut2004/System/UT2004.log for starters, but I doubt it'll help:

FOpenGLRenderInterface::SetDynamicStream <- SpriteIterator::Draw <- AxEmitter::Render <- FDynamicActor::Render <- FDynamicActor::Render <- FActorSceneNode::Render <- UCanvas::DrawActor <- UCanvas::execDrawActor <- UObject::ProcessEvent <- FPlayerSceneNode::Render <- UGameEngine::Draw <- USDLViewport::Repaint <- USDLClient::Tick <- ClientTick <- UGameEngine::Tick <- UpdateWorld <- MainLoop
Exit: Exiting.
Log: FileManager: Reading 0 GByte 60 MByte 729 KByte 961 Bytes from HD took 0.631757 seconds (0.631757 reading, 0.000000 seeking).
Log: FileManager: 0.000000 seconds spent with misc. duties
Uninitialized: Name subsystem shut down
Uninitialized: Allocation checking disabled
Uninitialized: Log file closed, Sun Feb 25 21:52:07 2007

---

### Post by 351W on 2007-03-07
A fresh install of Edgy seems to have cleared it right up.

---

