# unmanaged dedicated server hosting: What You Get, What You Fix Yourself, and Real Bare-Metal Pricing From $219/Month

Most people who search for unmanaged dedicated server hosting already know what they want: a whole physical machine, root access, and a monthly bill that doesn't include a surcharge for someone else to run `apt update` for them. What's usually less clear is where the line sits between your job and the provider's job, and why two servers that look identical on paper can differ by $100/month once you read the fine print.

This piece covers both sides of that: what "unmanaged" actually means in practice, what you should check on any provider before paying, and a concrete example using Sharktech's current bare-metal lineup — a provider whose own SLA states outright that all services are considered unmanaged unless otherwise noted. Their current plans run from $219 to $699/month depending on configuration and location, and their pricing page is public, which makes them a useful reference point for what the market looks like right now.

## What unmanaged dedicated server hosting actually includes

An unmanaged dedicated server is a physical machine leased to you alone. No virtualization layer, no noisy neighbors, no shared CPU quotas. You get the hardware, an network uplink, and a data center that keeps the machine powered, cooled, and connected. Everything above the hardware layer is yours.

The practical division of responsibility looks like this:

**The provider handles:**

- Physical hardware — if a RAM stick, drive, motherboard, or network card fails, they replace it. Sharktech, for example, commits in its SLA to replacing failed equipment at no cost within six hours of a verified helpdesk report.
- Network uptime — most providers guarantee a network availability figure. Sharktech's is 99.99%, with account credits if they miss it and you report it within ten business days.
- The uplink itself — port speed, the IP allocation, and (depending on the provider) baseline DDoS filtering.

**You handle:**

- OS installation, reinstallation, and patching
- Firewall configuration and general security hardening
- Backups and disaster recovery
- Every piece of software you run, and every 3 a.m. outage caused by a config mistake

That last point is the real trade. A managed plan moves the OS-layer work to the provider's staff and typically adds $50–150/month or more to the bill. Unmanaged keeps that money in your pocket but assumes you can diagnose a broken SSH config without opening a ticket first. If reading "you'll edit sshd_config" made you slightly nervous, that's useful information — it means you should either budget for a managed plan or plan to learn fast.

One detail worth knowing: many providers advertise "dedicated servers" that only give you OS-level access. True bare-metal plans hand you the hardware layer too, usually through an IPMI-style management console, which is what lets you mount a custom ISO and reinstall the OS yourself at 2 a.m. without waiting for anyone. Sharktech's dedicated plans are all bare-metal with a server management panel; not every provider does this, so it's worth checking.

## Who unmanaged dedicated server hosting is right for

The honest answer: people who already administer Linux (or BSD, or Windows Server) boxes somewhere, or teams with someone who does. That covers a wide range in practice:

- **Sysadmins and developers** who want full root on hardware they don't have to rack themselves, for CI runners, build servers, internal tooling, or a self-hosted stack
- **Game server operators**, who get attacked regularly and need both raw hardware and DDoS filtering that doesn't mean "we null-routed your IP, have a nice day"
- **Small hosting companies and agencies** reselling infrastructure, where the margin depends on not paying for management they'd redo themselves anyway
- **Teams migrating off hyperscalers** because a steady workload on AWS costs multiples of what the same compute costs on a dedicated box, with an invoice you need a spreadsheet to decode
- **Anyone with steady, predictable resource needs** — a dedicated server is at its best when utilization is constant; bursty workloads are a better fit for cloud

Who should stay away: anyone whose plan is "install WordPress and email support when something breaks." Without ops skills (or a budget for a freelance admin), the money you save on the plan you'll spend on the firefight. Managed hosting or a good VPS is the saner starting point there.

## What to check before you buy any unmanaged server

Budget bare-metal is a category with real traps. The sticker price is rarely the whole story, so run every candidate through this list:

1. **Setup fees.** Some providers charge $50–100 to "provision" a server you're going to configure yourself. Sharktech lists free setup on all its configurations; plenty of others don't. Check before checkout, not after.
2. **Bandwidth terms.** "Unmetered" on a 1Gbps port and "300TB/month metered" on a 10Gbps port are different products. Unmetered 1G means no overage fees but a hard ceiling on throughput (roughly ~330TB/month theoretical max). Metered 10G lets you burst far higher but caps total transfer. Neither is better in the abstract — match it to your traffic pattern.
3. **DDoS protection: included or upsold?** Many providers sell mitigation as an add-on or simply null-route your IP when an attack lands. Others, Sharktech included, bake baseline protection into every plan. If you're hosting anything with enemies — game servers, controversial sites, anything with a competitive community — this line item matters more than $20/month of RAM.
4. **IP allocations.** Check what IPv4 block comes standard and what extra addresses cost. IPv4 is a scarce commodity and per-IP fees add up.
5. **Refund policy.** Most dedicated providers, Sharktech included, are strictly no-refunds — their terms state all payments are nonrefundable, setup fees and all. That's normal for the industry, but it means the right move is starting with one smaller plan rather than pre-paying a year on hardware you haven't used.
6. **Hardware replacement terms.** Look for a stated replacement window in the SLA. "We'll fix it eventually" is not an SLA.
7. **Delivery time and stock.** Hardware shortages are real. Several of Sharktech's configurations are currently marked out of stock at various locations, and their site notes they can't guarantee sub-24-hour delivery for customized bare-metal. Ask about availability before you plan a migration weekend around a delivery date.

## A concrete example: Sharktech's current bare-metal lineup

Reading checklists is one thing; seeing actual configurations and prices is another. Sharktech has been around since 2003, runs its own network (they're an actual ISP, AS46844), and operates five data centers: Los Angeles, Las Vegas, Denver, Chicago, and Amsterdam. Their dedicated servers are unmanaged bare-metal by default — the SLA says all services are considered unmanaged unless expressly noted otherwise — with basic DDoS protection, a hardware management panel, free setup, and 24/7 support included on every plan.

Here is their full currently-advertised dedicated lineup, with monthly and annual-equivalent pricing (the Los Angeles lineup shown on their main dedicated servers page):

| Configuration | RAM | Storage | Network | Monthly | Annual (eff./mo) | Order |
| --- | --- | --- | --- | --- | --- | --- |
| Dual Xeon E5-2695v4 (36 × 2.1 GHz), 6× 2.5" SATA/SAS bays | 64GB DDR4 | 2TB M.2 NVMe | 10Gbps, 300TB/mo | $259 | $220.15 | [ Configure this server](https://portal.sharktech.net/aff.php?aff=1611&gid=94) |
| Dual Xeon E5-2695v4 (36 × 2.1 GHz), 6× 3.5" SATA/SAS bays | 64GB DDR4 | 2TB M.2 NVMe | 10Gbps, 300TB/mo | $269 | $228.65 | [ Request this configuration](https://bit.ly/SharKTech) |
| Dual Xeon Gold 6248 (40 × 2.5 GHz), 3× 3.5" bays | 128GB DDR4 | 2TB M.2 NVMe | 10Gbps, 300TB/mo | $299 | $254.15 | [ Order the Gold 6248](https://portal.sharktech.net/aff.php?aff=1611&gid=94) |
| Dual Xeon Gold 6248 (40 × 2.5 GHz), 6× 2.5" bays | 128GB DDR4 | 2TB M.2 NVMe | 10Gbps, 300TB/mo | $309 | $262.65 | [ Order this Gold 6248 build](https://portal.sharktech.net/aff.php?aff=1611&gid=94) |
| Dual Xeon Gold 6246 (24 × 3.3 GHz), 3× 3.5" bays | 128GB DDR4 | 2TB M.2 NVMe | 10Gbps, 300TB/mo | $309 | $262.65 | [ Order the Gold 6246](https://portal.sharktech.net/aff.php?aff=1611&gid=94) |
| Dual Xeon Gold 6248 (40 × 2.5 GHz), 6× U.2 bays | 128GB DDR4 | 2TB M.2 NVMe | 10Gbps, 300TB/mo | $329 | $296.10 | [ Order the U.2 NVMe build](https://portal.sharktech.net/aff.php?aff=1611&gid=94) |
| AMD EPYC 7702P (64 × 2 GHz), 10× U.2 bays | 128GB DDR4 | 2TB M.2 NVMe | 10Gbps, 300TB/mo | $499 | $424.15 | [ Order the EPYC 7702P](https://portal.sharktech.net/aff.php?aff=1611&gid=94) |
| Dual AMD EPYC 7702 (128 × 2 GHz), 10× U.2 bays | 128GB DDR4 | 2TB M.2 NVMe | 10Gbps, 300TB/mo | $699 | $594.15 | [ Get a dual-EPYC quote](https://bit.ly/SharKTech) |

A few things the table doesn't show:

- Every configuration is upgradeable at order time or later — RAM up to 1TB, additional NVMe, SATA SSDs/HDDs in the open bays, and network upgrades to 40G and 100G.
- The order form lets you pick the OS (Linux options install at no extra cost; for Windows you bring your own license) and add a control panel license if you want one — that's a paid add-on, so factor it in if your workflow depends on cPanel rather than a shell.
- Sharktech also offers a GPU bare-metal category in Las Vegas (a Dual Xeon E5-2695v4 with an RTX A4000 and 256GB RAM listed at $1,557/quarter, about $519/month), though it's currently out of stock — a reminder to check availability for anything specialized.

If you want to browse the full live list — including what's in stock this week — you can [👉 view all Sharktech bare-metal configurations](https://portal.sharktech.net/aff.php?aff=1611&gid=94).

## Location pricing and billing cycles: where the real savings are

The headline prices above are the Los Angeles lineup. Sharktech prices the same hardware differently by data center, and the differences aren't trivial. The Dual Xeon E5-2695v4 with 64GB — $259/month in Los Angeles — starts at $219/month in Denver and Las Vegas. The single-socket EPYC 7702P drops from $499 to $459 in Denver, Las Vegas, and Chicago. Amsterdam, their one European location, generally tracks the LA pricing.

That means if your users aren't latency-sensitive to a specific coast, Denver or Las Vegas gets you identical hardware for $40/month less. Over a year that's $480, which is most of a month's payment.

The billing cycle discounts are the other lever. Committing longer cuts the rate at every tier: quarterly billing is 5% off, semi-annual is 10% off, and annual is 15% off — which is how the $259/month E5-2695v4 becomes $2,641.80/year, effectively $220.15/month. Same math applies across the lineup. Given that the no-refund policy applies to whatever you prepay, the sane sequence is: test on monthly billing for a month or two, then switch the billing cycle once you know the hardware and network work for you.

To compare the same configs in the cheaper locations directly, you can [👉 check Denver's dedicated server pricing](https://portal.sharktech.net/aff.php?aff=1611&gid=93), [👉 look at Las Vegas plans](https://portal.sharktech.net/aff.php?aff=1611&gid=118), or [👉 browse the Amsterdam lineup](https://portal.sharktech.net/aff.php?aff=1611&gid=91).

## The honest limitations

No provider review is worth much without the downsides, so here are Sharktech's, based on their own published terms and third-party feedback:

- **No refunds, period.** Their terms are explicit: all payments are nonrefundable, including setup fees and monthly charges. There's no money-back window. Start monthly, not annual.
- **Support scope is infrastructure, not your software.** The team is there 24/7 for network, hardware, and panel issues. They are not there to fix your nginx config, and they don't pretend to be. That's the unmanaged deal.
- **Stock is genuinely variable.** As of this writing, multiple configurations across several locations show "out of stock," and the site warns that custom bare-metal can't be guaranteed in under 24 hours. If you need a specific config by a specific date, contact sales first.
- **Third-party feedback is a small sample.** Sharktech holds a 3.5/5 average on Trustpilot from 13 reviews — praise concentrates on DDoS protection and reliability, complaints on support depth for complex issues. Thirteen reviews is thin evidence in either direction; the SLA commitments and public pricing are more solid ground for a decision than the review count.
- **Windows licensing is on you.** Linux is free to install; Windows requires your own key.

None of these are hidden gotchas — they're all stated plainly in Sharktech's own terms — but they shape what kind of buyer this works for.

## Quick decision guide

Mapping situations to configurations, using the verified pricing:

| Your situation | Sensible starting point |
| --- | --- |
| Dev environment, CI runner, or a first dedicated box | Dual Xeon E5-2695v4 / 64GB in Denver or Las Vegas at $219/mo |
| Virtualization host or busy web/database stack | Dual Xeon Gold 6248 / 128GB at $259–299/mo depending on location |
| High clock-speed workloads (game servers, per-core licensing) | Dual Xeon Gold 6246 at $309/mo — 3.3 GHz base clocks vs 2.5 on the 6248 |
| Heavy parallel workloads, big virtualization, render farms | EPYC 7702P (64 cores) at $459–499/mo, or dual EPYC at $699/mo |
| Anything needing bulk NVMe storage | The U.2 bay builds — 6 or 10 U.2 slots for multi-terabyte NVMe arrays |
| Something not on the list | Sales builds custom configs to order, sourced through their vendors |

## Frequently asked questions

**Is unmanaged cheaper than managed, really?**

On the invoice, yes — typically $50–150/month less for identical hardware. In total cost of ownership, only if your time (or your admin's time) is cheaper than the managed-plan premium. For people who already run servers, the managed premium buys nothing they need.

**What happens if the hardware dies?**

The provider replaces it — that's their side of the unmanaged line. Sharktech commits to replacing failed RAM, CPUs, drives, motherboards, and network cards at no cost within six hours of a verified report. What nobody replaces is your data. Backups are entirely your responsibility, and this is the single most common way unmanaged-server users get hurt.

**Can I run Windows?**

On Sharktech, yes, with your own license. Linux distributions and BSD install at no additional cost. If you're comfortable in Linux, there's rarely a reason to pay for Windows on a server you administer yourself.

**Is DDoS protection actually included, or is it a teaser?**

At Sharktech, baseline protection is included on every plan — their order forms show "Basic DDoS Protection" as a standard item, with a 100Gbps protection tier available as an upgrade for heavier attack profiles. Many competitors sell this as an add-on, so it's a genuine differentiator if attacks are in your threat model.

**How fast is delivery?**

For readily available configurations, typically fast; for anything customized or currently out of stock, it depends on hardware availability, and Sharktech explicitly says sub-24-hour delivery can't be guaranteed for custom bare-metal. Check stock and ask sales before scheduling a migration around a delivery date.

## The short version

Unmanaged dedicated server hosting is a good deal precisely because it's a narrow deal: you get real hardware, real network, and real uptime commitments, and in exchange you own everything that happens above the kernel. If you have the skills — or the willingness to acquire them — you save meaningful money every month compared to managed plans and hyperscaler bills alike.

If you want to see whether Sharktech's specific combination (unmanaged bare-metal from $219/month, included DDoS protection, free setup, five locations) fits your workload, you can [👉 browse the live configurations and current availability](https://portal.sharktech.net/aff.php?aff=1611&gid=94) — and for anything the standard lineup doesn't cover, [👉 their sales team quotes custom builds](https://bit.ly/SharKTech), usually within hours.
