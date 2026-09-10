# ProductPilot AI

## Project Identity

ProductPilot AI is an AI-powered e-commerce product intelligence platform.

The platform helps sellers discover products worth selling, evaluate product opportunities, calculate profitability, improve product positioning, and generate optimized marketplace listings.

The initial target market is Etsy sellers.

The architecture must remain marketplace-agnostic so the platform can later support Shopify, Amazon, eBay, TikTok Shop, and direct-to-consumer brands.

---

# 1. PRIMARY OBJECTIVE

Build a commercially viable SaaS product that helps e-commerce sellers make better product decisions.

The core user journey is:

Discover
→ Research
→ Score
→ Validate
→ Calculate Profit
→ Improve
→ Generate Listing
→ Save
→ Monitor
→ Act

The product must prioritize actionable business intelligence over generic AI text generation.

The user should leave an analysis knowing:

1. What product they could sell.
2. Why the product may be attractive.
3. Who may buy it.
4. How competitive the opportunity is.
5. What price range may make sense.
6. What the estimated economics look like.
7. How they could differentiate it.
8. What they should do next.

---

# 2. PRODUCT PRINCIPLES

Follow these principles in every implementation.

## Principle 1: Solve a business problem

Do not build features simply because AI can build them.

Every feature must answer:

"What decision does this help the seller make?"

## Principle 2: Action over information

The product should turn research into recommendations.

Bad:

"Here are 20 products."

Good:

"These 5 products have the strongest opportunity based on the available evidence."

## Principle 3: Evidence over speculation

Never present estimates as verified facts.

Clearly distinguish:

- Verified data
- User-provided data
- Calculated estimates
- AI-generated recommendations
- Assumptions
- Unknown information

## Principle 4: No fabricated market data

Never invent:

- Search volume
- Sales volume
- Revenue
- Competitor counts
- Market size
- Pricing data
- Trends
- Product demand

If the platform does not have reliable data, say so.

## Principle 5: Minimal viable complexity

Do not over-engineer.

Build the smallest correct solution.

Do not create abstractions for hypothetical future requirements.

Do not add features outside the current task unless they are required for correctness, security, or maintainability.

## Principle 6: Production quality

All production features must include:

- Error handling
- Validation
- Loading states
- Empty states
- Authentication where required
- Authorization
- Tests
- Mobile responsiveness
- Accessibility
- Observability where appropriate

## Principle 7: User trust

The application handles business decisions.

Accuracy and transparency are more important than impressive language.

---

# 3. DEFAULT TECH STACK

Preferred stack:

- Next.js
- TypeScript
- React
- Tailwind CSS
- shadcn/ui
- Supabase
- PostgreSQL
- Stripe
- Vercel
- GitHub
- Anthropic API

Use the current stable versions available when implementation begins.

Do not downgrade dependencies without a specific compatibility reason.

Do not introduce another framework unless there is a clear technical requirement.

---

# 4. ARCHITECTURE RULES

Use clear separation between:

Presentation
→ Application logic
→ Domain logic
→ Data access
→ External services

Do not place business logic directly inside UI components.

Do not expose secret keys to client-side code.

Use server-side operations for:

- AI API calls
- Stripe operations
- privileged database operations
- external API credentials
- sensitive calculations

---

# 5. AI DEVELOPMENT RULES

AI is a component of ProductPilot, not the product itself.

AI output must use structured schemas whenever possible.

Prefer:

JSON schema
→ validation
→ business rules
→ database persistence
→ UI

over:

Prompt
→ raw text
→ UI

AI-generated content must be validated before being displayed as structured application data.

Never trust AI output blindly.

---

# 6. INVESTIGATION BEFORE IMPLEMENTATION

Before modifying existing code:

1. Inspect the repository.
2. Locate relevant files.
3. Understand existing architecture.
4. Inspect package.json.
5. Inspect database schema.
6. Inspect environment configuration without exposing secrets.
7. Inspect existing tests.
8. Determine whether the requested behavior already exists.
9. Implement the smallest correct change.

Never speculate about code that has not been inspected.

If a user references a specific file, read it before modifying it.

---

# 7. DEVELOPMENT WORKFLOW

For every meaningful task:

## Phase 1: Understand

Determine:

- What is being requested?
- Why is it needed?
- Which files are affected?
- Which systems are affected?
- What could break?

## Phase 2: Plan

Create a concise implementation plan.

Identify:

- Files to change
- Database changes
- API changes
- UI changes
- Tests
- Deployment implications

## Phase 3: Implement

Implement the smallest complete solution.

## Phase 4: Verify

Run:

- Type checking
- Linting
- Unit tests
- Integration tests where applicable
- Build
- Relevant end-to-end tests

## Phase 5: Review

Check:

- Security
- Accessibility
- Mobile layout
- Error handling
- Performance
- Data integrity
- AI output validation

## Phase 6: Report

State:

- What changed
- What was tested
- What passed
- What remains
- Any risks

---

# 8. GIT RULES

Use small logical commits.

Commit messages should describe the actual change.

Examples:

feat: add product opportunity analysis

feat: add profit calculator

fix: validate product analysis output

test: add opportunity scoring tests

Never force push.

Never reset or delete work that was not created by you.

Do not overwrite unfamiliar user changes.

---

# 9. DATABASE RULES

Database migrations must be explicit.

Never modify production schema manually without a migration.

Every table should have appropriate:

- Primary key
- Foreign keys
- Indexes
- Timestamps
- Ownership relationships
- Row-level security where applicable

Users must only access records they are authorized to access.

---

# 10. SECURITY RULES

Never expose:

- API keys
- Service-role credentials
- Stripe secrets
- Database passwords
- OAuth secrets
- Internal system prompts

Never place secrets in:

- Client bundles
- Git
- Markdown files
- Test fixtures
- Logs

Validate all external input.

Protect against:

- Prompt injection
- SQL injection
- XSS
- CSRF where relevant
- Unauthorized data access
- File upload abuse
- Excessive AI usage
- Rate-limit abuse

---

# 11. AI COST CONTROL

Every AI feature must have a defined cost strategy.

Use:

- Model routing
- Token limits
- Structured outputs
- Caching where appropriate
- Request deduplication
- Usage limits
- User quotas

Do not call an expensive model when a smaller model can reliably perform the task.

---

# 12. UX RULES

The interface should feel like a professional business intelligence product.

Avoid generic AI dashboard design.

Do not use:

- Excessive gradients
- Generic AI imagery
- Unnecessary animations
- Cluttered dashboards
- Excessive cards
- Fake statistics

Prioritize:

- Clear hierarchy
- Useful data visualization
- Strong typography
- Fast interactions
- Obvious actions
- Good mobile behavior

---

# 13. PRODUCT PRIORITY

Prioritize features in this order:

P0:
- Authentication
- Dashboard
- Product research
- Opportunity analysis
- Product scoring
- Profit calculator
- Listing generator
- Usage tracking
- Billing

P1:
- Product saving
- Product history
- Image analysis
- Competitor analysis
- Export

P2:
- Marketplace integrations
- Monitoring
- Alerts
- Team accounts
- Agency functionality

Do not build P1 or P2 functionality when unfinished P0 functionality remains.

---

# 14. MVP DEFINITION

The MVP must allow a user to:

1. Create an account.
2. Start a product analysis.
3. Enter product/niche information.
4. Receive a structured opportunity report.
5. View an opportunity score.
6. View assumptions and evidence.
7. Calculate estimated profitability.
8. Generate an optimized listing.
9. Save the result.
10. Return to the dashboard.
11. Understand their remaining usage.
12. Upgrade to a paid plan.

---

# 15. DEFINITION OF DONE

A feature is not complete because the code exists.

A feature is complete when:

- Requirements are implemented.
- UI works on mobile and desktop.
- Inputs are validated.
- Errors are handled.
- Database operations are secure.
- AI output is validated.
- Tests pass.
- Build passes.
- No obvious console errors remain.
- Documentation is updated where necessary.

---

# 16. AUTONOMOUS AGENT BEHAVIOR

When given a clear implementation task:

Investigate
→ Plan
→ Implement
→ Test
→ Review
→ Fix
→ Verify

Do not stop after writing code.

Do not report success merely because code compiled.

Verify actual behavior.

If independent tasks can be executed in parallel, prefer parallel execution.

If an action is destructive, irreversible, production-impacting, or affects shared infrastructure, request confirmation before performing it.

---

# 17. PRODUCT TRUTH

The platform is not allowed to promise that a product will sell.

Use language such as:

- Opportunity
- Estimate
- Signal
- Evidence
- Potential
- Recommendation
- Confidence

Avoid unsupported claims such as:

- Guaranteed winner
- Guaranteed sales
- Guaranteed profit
- Guaranteed demand

---

# 18. CURRENT BUSINESS GOAL

Launch a usable paid MVP quickly.

The initial objective is:

Get real sellers using ProductPilot.

Then:

Observe behavior
→ identify the most valuable feature
→ improve it
→ increase conversion
→ increase retention
→ expand functionality

Revenue and user feedback should determine roadmap priorities.

---

# 19. DOCUMENTATION HIERARCHY

When requirements conflict, use this priority:

1. Security
2. Database integrity
3. PRD
4. Product architecture
5. Business rules
6. UX specifications
7. Implementation preferences

If two documents conflict, flag the conflict instead of silently choosing.

---

# 20. FINAL RULE

Build a simple product that solves a real seller problem.

Do not build a complicated product to demonstrate technical capability.
