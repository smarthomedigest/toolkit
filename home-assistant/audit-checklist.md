# Home Assistant Audit Checklist

A structured checklist for auditing your Home Assistant installation. Works great as a manual walkthrough or as a guide for AI-assisted audits (see our [AI Digest article](https://smarthomedigest.com/articles/ai-digest-1-claude-code-home-assistant-audit) for the full process).

## System Health

- [ ] **HA Core version** — Are you on the latest stable release?
- [ ] **HA OS version** — Check for pending OS updates
- [ ] **Supervisor status** — Healthy, no pending updates?
- [ ] **Storage usage** — Is disk usage under 80%? (especially on HA Green/Pi)
- [ ] **Memory usage** — Any signs of memory pressure?
- [ ] **Database size** — Is `home-assistant_v2.db` growing out of control? Consider recorder purge settings

## Integrations

- [ ] **List all integrations** — Do you know what each one does?
- [ ] **Remove unused integrations** — If you uninstalled a device, did you remove the integration?
- [ ] **Check for deprecated integrations** — Some get replaced or removed between versions
- [ ] **Custom components (HACS)** — Are they maintained? Check last commit dates
- [ ] **Integration errors** — Check Settings → System → Logs for integration-specific errors

## Automations

- [ ] **Review all automations** — Can you explain what each one does?
- [ ] **Disable unused automations** — Don't delete, disable first (you might want them back)
- [ ] **Check for broken automations** — Look for automations referencing deleted entities
- [ ] **Safety-critical automations** — Leak sensors, smoke detectors, door locks — test these manually
- [ ] **Notification automations** — Do they actually deliver? Test each notification target
- [ ] **Automation mode** — Are `single`/`restart`/`queued`/`parallel` modes set appropriately?

## Devices & Entities

- [ ] **Unavailable entities** — Check Developer Tools → States, filter for "unavailable"
- [ ] **Unknown entities** — Same check for "unknown" state
- [ ] **Dead devices** — Devices that haven't reported in weeks
- [ ] **Naming consistency** — Are entity names logical and findable?
- [ ] **Areas assigned** — Are devices organized into areas/rooms?

## Network & Protocols

- [ ] **Zigbee mesh health** — Check your coordinator and router coverage (ZHA/Z2M)
- [ ] **Z-Wave mesh health** — Node status, dead nodes, heal network if needed
- [ ] **Wi-Fi device connectivity** — Any devices dropping offline frequently?
- [ ] **DNS resolution** — Can HA resolve external hostnames? (matters for cloud integrations)

## Security

- [ ] **External access** — Is remote access configured securely? (Nabu Casa, reverse proxy, VPN)
- [ ] **User accounts** — Remove unused accounts, use strong passwords
- [ ] **Long-lived access tokens** — Audit and revoke unused tokens
- [ ] **Add-on security** — Are add-ons up to date? Any with unnecessary network access?
- [ ] **Backups** — Are automatic backups configured? Test a restore!

## Logs & Errors

- [ ] **Review recent logs** — Check for recurring errors or warnings
- [ ] **High-frequency errors** — Anything spamming the log? (Fix or filter it)
- [ ] **Deprecated warnings** — Address these before they become breaking changes
- [ ] **Integration reconnection loops** — Signs of unstable connections

## Performance

- [ ] **Recorder configuration** — Exclude high-frequency entities you don't need history for
- [ ] **Dashboard load time** — Are dashboards snappy or sluggish?
- [ ] **Automation execution time** — Any automations that take too long to trigger?

## Backup & Recovery

- [ ] **Backup schedule** — Automated backups configured?
- [ ] **Backup storage** — Backups stored off-device? (network share, cloud)
- [ ] **Backup tested** — Have you actually restored from a backup?
- [ ] **Configuration documented** — Could you rebuild from scratch if needed?

---

## How to Use This Checklist

1. **Copy this file** to your own repo or notes app
2. **Work through it section by section** — don't try to do everything at once
3. **Prioritize safety-critical items** — leak sensors, smoke detectors, locks
4. **Schedule regular audits** — quarterly is a good cadence
5. **Track what you find** — document issues and fixes for future reference

## AI-Assisted Auditing

For a detailed walkthrough of using AI coding agents (like Claude Code) to automate much of this checklist, read our article:
[AI Digest #1: Claude Code Meets Home Assistant](https://smarthomedigest.com/articles/ai-digest-1-claude-code-home-assistant-audit)

---

*From [Smart Home Digest](https://smarthomedigest.com) — independent smart home reviews and guides.*
