# Dozen Updates

Auto-update hosting for the Dozen macOS app via [Sparkle](https://sparkle-project.org/).

## Files

- `appcast.xml` - Update feed consumed by Sparkle

## Releasing Updates

1. Build new version of Dozen (bump version in Info.plist)
2. Build DMG: `./scripts/build-dmg.sh`
3. Get DMG file size: `stat -f%z build/Dozen-Installer.dmg`
4. Create GitHub Release in this repo, upload DMG
5. Update `appcast.xml` with new version entry
6. Push changes to main branch

## Appcast Entry Template

```xml
<item>
  <title>Version X.Y.Z</title>
  <sparkle:version>BUILD_NUMBER</sparkle:version>
  <sparkle:shortVersionString>X.Y.Z</sparkle:shortVersionString>
  <pubDate>DAY, DD MMM YYYY HH:MM:SS +0000</pubDate>
  <enclosure url="https://github.com/sebp90/dozen-updates/releases/download/vX.Y.Z/Dozen-Installer.dmg"
             length="FILE_SIZE_BYTES"
             type="application/octet-stream"/>
</item>
```
