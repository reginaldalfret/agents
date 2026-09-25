---
"agents": patch
---

Downgrade MCPClientManager discovery failure log from error to warn

The `connectToServer` path logs discovery failures (including recoverable
timeouts) at `console.error` level. Fleet alerting keyed on error-level
logs fires false positives because the caller already recovers from these
failures. This patch downgrades the log to `console.warn` so monitoring
systems can distinguish true errors from expected transient conditions.

Fixes #2300
