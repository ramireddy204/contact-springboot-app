
AI-Assisted Development Guidelines
1. Purpose
This file defines the mandatory instructions for AI coding agents and AI-assisted development tools working in this repository.

AI tools must follow these instructions when:

Creating new code
Modifying existing code
Fixing defects
Refactoring code
Writing tests
Creating documentation
Updating configuration
Updating infrastructure code
Reviewing code
Creating or updating APIs
Updating dependencies
AI-generated code must meet the same engineering, security, testing, and review standards as developer-written code.

2. Core Principles
All AI-assisted development must follow these principles:

Understand before modifying.
Inspect existing code before generating new code.
Follow existing architecture and coding patterns.
Make the smallest safe change required.
Prefer existing components, utilities, and dependencies.
Do not introduce unnecessary complexity.
Never compromise security for convenience.
Write or update tests for behavioral changes.
Validate generated code before considering the task complete.
Keep a human developer responsible for the final change.
AI-generated output must never be assumed correct without validation.

3. Instruction Priority
Before starting a development task, inspect the applicable project instructions.

Follow instructions in this order when applicable:

Security and compliance requirements
Repository-level AGENTS.md
Directory-specific AGENTS.md
Project architecture standards
Coding standards
Framework-specific guidelines
Approved AI skills/workflows
Task-specific prompts
Existing implementation patterns
If instructions conflict, use the higher-priority instruction and report the conflict to the developer.

Do not silently ignore conflicting requirements.

4. Understand the Requirement First
Before modifying code:

Understand the requested behavior.
Identify the acceptance criteria.
Determine the affected application areas.
Identify relevant existing implementations.
Identify dependencies.
Consider security implications.
Determine testing requirements.
Determine backward-compatibility impact.
Do not immediately generate code when the requirement requires investigation.

For unclear requirements, state assumptions explicitly.

5. Inspect Existing Implementation
Before creating new components or functionality, search the repository for similar implementations.

Inspect:

Existing components
Services
Controllers
APIs
DTOs
Models
Utilities
Repositories
Tests
Configuration
Error-handling patterns
Logging patterns
Security controls
Prefer reuse over duplication.

Do not introduce a new architectural pattern when an established project pattern already solves the requirement.

6. Implementation Planning
For non-trivial changes, create a short implementation plan before modifying code.

Example:

Identify impacted modules.
Update data model or DTO.
Implement validation.
Update business logic.
Update API/controller.
Add or update tests.
Run quality checks.
Review the final diff.
For large features, use:

requirements ↓ design ↓ implementation plan ↓ implementation ↓ testing ↓ review

Avoid making large unrelated changes.

7. Coding Standards
All generated or modified code must:

Follow existing naming conventions.
Follow repository formatting rules.
Be readable and maintainable.
Follow SOLID principles where appropriate.
Avoid unnecessary duplication.
Avoid unnecessary abstraction.
Maintain clear separation of concerns.
Include appropriate error handling.
Include appropriate logging.
Use meaningful variable and method names.
Avoid unexplained magic values.
Follow established framework conventions.
Do not rewrite working code unless required by the task.

8. Change Scope
Use the principle:

Make the smallest safe change necessary to satisfy the requirement.

Do not perform unrelated:

Refactoring
Formatting
Renaming
Dependency upgrades
Architecture changes
Configuration changes
Performance optimizations
unless explicitly required.

Keeping changes focused makes AI-generated changes easier to review and safer to integrate.

9. Frontend Guidelines
For Angular and TypeScript development:

Follow the Angular version and patterns already used by the project.
Use strict TypeScript typing.
Avoid any unless there is a valid reason.
Follow existing component structure.
Reuse shared components.
Reuse existing pipes and directives.
Reuse existing services.
Follow existing state-management patterns.
Follow existing dependency-injection patterns.
Keep business logic outside presentation components where appropriate.
Follow existing routing conventions.
Follow existing form patterns.
Follow existing localization/i18n conventions.
Follow project accessibility requirements.
Avoid duplicating frontend utilities.
Prefer:

Component ↓ Facade / Service ↓ HTTP/API layer

when consistent with the existing application architecture.

Do not introduce new state-management libraries or UI frameworks without explicit approval.

10. Backend Guidelines
For Java and Spring Boot development:

Follow existing project layering and architecture.

Typical structure:

Controller ↓ Service ↓ Repository ↓ Database / External Service

When applicable:

Use DTOs for API boundaries.
Validate incoming requests.
Use existing validation mechanisms.
Keep business logic out of controllers.
Use dependency injection.
Follow existing exception-handling mechanisms.
Use centralized exception handling where established.
Follow existing logging conventions.
Reuse repository patterns.
Follow existing transaction-management patterns.
Avoid exposing internal implementation details through APIs.
Do not expose:

Stack traces
Internal exceptions
Credentials
Tokens
Database details
Sensitive customer information
in API responses.

11. API Development
When creating or modifying APIs:

Follow existing REST/API conventions.
Maintain backward compatibility unless explicitly changed.
Validate input.
Handle invalid requests appropriately.
Handle expected error scenarios.
Follow established HTTP status-code conventions.
Follow existing authentication mechanisms.
Follow existing authorization mechanisms.
Update API documentation where applicable.
Evaluate:

Happy path
Invalid input
Missing input
Unauthorized access
Forbidden access
Resource not found
Duplicate requests
Backend failures
External-service failures
12. Security Requirements
Security requirements are mandatory.

Never:

Hard-code passwords.
Hard-code API keys.
Hard-code access tokens.
Commit secrets.
Expose credentials.
Log authentication tokens.
Log passwords.
Log sensitive customer information unnecessarily.
Disable security controls to make tests pass.
Bypass authorization.
Disable certificate validation without explicit authorization.
Validate external input.

Consider risks including:

Injection attacks
Broken authorization
Authentication weaknesses
Sensitive-data exposure
Command injection
Path traversal
Unsafe deserialization
Cross-site scripting
Cross-site request forgery
Insecure dependencies
Secret exposure
Use project-approved secret-management mechanisms.

13. Sensitive and Customer Data
Treat sensitive information carefully.

Do not expose sensitive data through:

Logs
Error messages
Debug output
Tests
Mock datasets
Documentation
Prompt content
AI-generated examples
Use synthetic test data whenever real customer data is unnecessary.

Never send confidential information to external tools unless explicitly permitted by organizational policy.

14. Dependencies
Before adding a dependency:

Determine whether existing project capabilities solve the requirement.
Check whether an existing dependency provides the capability.
Confirm the dependency is actually necessary.
Follow project dependency-management policies.
Do not add dependencies merely to reduce a few lines of code.

Never change dependency versions unrelated to the requested task unless required.

Report every newly introduced dependency in the final summary.

15. Testing Requirements
Every behavioral change should include appropriate testing.

Consider:

Unit tests
Component tests
Integration tests
API tests
End-to-end tests
Tests should cover:

Normal scenarios
Error scenarios
Validation failures
Boundary conditions
Important edge cases
Do not delete or weaken tests simply to make generated code pass.

Do not modify assertions unless the expected behavior genuinely changed.

16. Bug Fixes
When fixing a defect:

Understand the reported issue.
Locate the root cause.
Do not merely suppress the symptom.
Identify affected code.
Implement the smallest appropriate fix.
Add or update a regression test.
Run affected tests.
Check for similar issues in related code.
When possible, the regression test should fail before the fix and pass afterward.

17. Refactoring
Refactoring must preserve observable behavior unless behavioral changes are explicitly requested.

When refactoring:

Keep the scope focused.
Preserve public contracts.
Preserve API compatibility where required.
Run existing tests.
Avoid combining large refactoring with unrelated feature changes.
Do not perform speculative refactoring.

18. Error Handling
Do not silently ignore errors.

Handle errors using established project conventions.

Errors should:

Provide useful diagnostic information.
Avoid leaking sensitive information.
Be logged at an appropriate level.
Be mapped to appropriate API/application behavior.
Avoid empty catch blocks.

Do not catch broad exceptions unless necessary.

19. Logging
Follow project logging standards.

Logs should help diagnose operational problems without exposing confidential information.

Use appropriate levels:

DEBUG
INFO
WARN
ERROR
Do not log:

Passwords
Authentication tokens
API secrets
Sensitive personal information
Complete sensitive request/response payloads
Avoid unnecessary logging inside high-frequency loops.

20. Configuration
Follow established configuration-management patterns.

Do not:

Hard-code environment-specific values.
Hard-code URLs when configuration already exists.
Hard-code secrets.
Duplicate configuration values.
Modify production configuration unnecessarily.
Use existing environment and configuration mechanisms.

21. Cloud and AWS Changes
For AWS-related changes:

Follow existing infrastructure patterns.
Apply least-privilege access principles.
Reuse existing IAM roles and policies where appropriate.
Avoid wildcard permissions unless explicitly justified.
Do not hard-code credentials.
Follow project resource-naming conventions.
Consider environment separation.
Consider logging and monitoring.
Consider failure and retry behavior.
Consider cost impact when relevant.
Infrastructure changes must receive the same review rigor as application code.

22. Database Changes
For database changes:

Follow existing migration mechanisms.
Avoid destructive changes unless explicitly approved.
Consider backward compatibility.
Consider existing data.
Consider rollback requirements.
Consider indexing and performance impact.
Avoid embedding credentials in database configuration.
Use established transaction patterns.
Do not modify production data directly unless specifically authorized.

23. AI Prompts
Use structured prompts where available.

Preferred prompt structure:

Objective
Clearly describe the required outcome.

Context
Describe relevant application/module context.

Requirements
List functional requirements.

Constraints
Specify architecture, security, compatibility, or technical constraints.

Acceptance Criteria
Define conditions that determine successful completion.

Validation
Specify tests and quality checks that must be executed.

Avoid vague prompts such as:

"Fix the code."

Prefer:

"Identify the root cause of the failing customer creation workflow, implement the smallest safe fix following existing service and validation patterns, add a regression test, run relevant validation, and summarize the changes."

24. Skills and Reusable AI Workflows
Use approved skills or reusable workflows when they match the task.

Examples may include:

Feature implementation
Angular development
Spring Boot API development
Unit-test creation
Integration testing
Security review
Code review
Bug investigation
Database migration
Documentation
Performance analysis
Before invoking a reusable workflow:

Verify that it applies to the requested task.
Follow its documented instructions.
Do not bypass repository-level requirements.
Repository instructions override convenience.

25. Hooks and Automated Guardrails
Respect all configured repository hooks and automated controls.

Hooks may perform activities such as:

Policy validation
Tool validation
Security checks
Secret scanning
Command restrictions
Audit logging
Quality checks
Post-execution validation
Never:

Disable hooks to complete a task.
Modify hooks to bypass policy.
Circumvent blocked operations.
Ignore failed security checks.
If a hook blocks an operation, identify and resolve the underlying problem.

26. Tool and Command Safety
Before executing commands:

Understand what the command does.
Prefer read-only inspection before modification.
Avoid destructive commands.
Scope commands narrowly.
Verify paths and targets.
Do not execute destructive operations unless explicitly required and permitted.

Examples requiring special care include:

Recursive deletion
Database deletion
Force pushes
Branch history rewriting
Production deployments
Infrastructure destruction
Permission modifications
Secret manipulation
Never circumvent repository protections.

27. AI-Assisted Development Workflow
Use the following workflow for non-trivial development tasks:

Requirement ↓ Understand ↓ Read Instructions ↓ Inspect Existing Implementation ↓ Plan ↓ Implement ↓ Test ↓ Security / Quality Validation ↓ Review Diff ↓ Human Review ↓ CI/CD Validation

Each stage is required when applicable.

28. Build and Validation
Before considering work complete, run the relevant project-defined validation commands.

Examples may include:

Frontend:

npm test npm run lint npm run build

Backend:

mvn test mvn verify

Use the actual commands defined by this repository.

Do not invent or assume build commands when project documentation provides them.

If a validation command cannot be executed, report that clearly.

29. Static Analysis and Security Scanning
Run applicable project-configured checks.

These may include:

Linting
Static analysis
Dependency scanning
Secret scanning
Vulnerability scanning
Code-quality checks
Do not suppress legitimate findings simply to make validation pass.

Fix findings within the scope of the requested change where appropriate.

Report unresolved findings.

30. Review the Diff
Before completing a task, review all generated changes.

Check for:

Incorrect functionality
Unrequested changes
Architecture violations
Security vulnerabilities
Missing input validation
Missing error handling
Duplicate logic
Dead code
Unnecessary dependencies
Performance problems
Missing tests
Debug statements
Sensitive information
Backward-compatibility problems
Remove accidental or unrelated modifications.

31. Documentation
Update documentation when a change affects:

Public APIs
Configuration
Environment variables
Architecture
Setup instructions
Deployment procedures
Developer workflows
Operational procedures
Do not create unnecessary documentation for trivial implementation details.

Keep documentation consistent with actual behavior.

32. Git and Pull Request Guidelines
Keep commits and pull requests focused on the requested change.

Avoid:

Unrelated formatting
Unnecessary generated files
Debug artifacts
Secrets
Temporary files
Unrelated dependency changes
Pull-request descriptions should explain:

What changed
Why it changed
How it was tested
Important assumptions
Risks
Newly introduced dependencies
Compatibility considerations
AI-generated changes must follow the normal review process.

33. AI Self-Review
Before declaring work complete, perform a self-review.

Check:

Did I satisfy the requirement?
Did I follow AGENTS.md?
Did I follow existing architecture?
Did I introduce unnecessary changes?
Did I introduce security risks?
Did I expose sensitive information?
Did I add appropriate validation?
Did I implement appropriate error handling?
Did I add/update tests?
Did relevant tests pass?
Did lint/static analysis pass?
Did the build pass?
Did I introduce new dependencies?
Is backward compatibility preserved where required?
Is documentation still accurate?
Fix identified problems before completion where they fall within the requested scope.

34. Completion Report
At the end of an AI-assisted coding task, provide a concise summary.

Changes
List files/components changed and the reason.

Tests
List tests added or updated.

Validation
List commands/checks executed and their results.

Dependencies
List newly added dependencies.

Write:

None

if none were introduced.

Assumptions
List assumptions made during implementation.

Risks / Follow-up
List unresolved risks or required manual validation.

Do not claim a test, build, or security scan passed unless it was actually executed successfully.

35. Definition of Done
An AI-assisted change is complete only when applicable requirements below have been satisfied.

Requirement understood
Acceptance criteria satisfied
AGENTS.md followed
Existing architecture followed
Coding standards followed
Change scope kept focused
Security requirements followed
No secrets introduced
Input validation implemented
Error handling reviewed
Unit tests updated
Integration tests considered
Regression tests added for bug fixes
Relevant tests passed
Lint checks passed
Build passed
Static/security checks completed
Dependencies reviewed
Final diff reviewed
Documentation updated where necessary
Assumptions documented
Remaining risks documented
Human review completed before merge
36. Golden Rules
The following rules take precedence during AI-assisted development:

Understand before modifying.

Inspect before generating.

Reuse before creating.

Make the smallest safe change.

Never trade security for convenience.

Never bypass repository guardrails.

Never claim validation that was not performed.

AI generates. Developers verify. Automation validates. Reviewers approve.

37. Project-Specific Configuration
Update this section for the repository.

Project
Project Name: <PROJECT_NAME>

Technology Stack
Frontend:

<Angular / React / Other>
Backend:

<Java / Spring Boot / Node.js / NestJS / Other>
Database:

<Database>
Cloud:

<AWS / Azure / Other>
Architecture
<Describe architecture or link to architecture documentation>

Build Commands
Frontend:

<command>

Backend:

<command>

Test Commands
Frontend:

<command>

Backend:

<command>

Lint Commands
<command>

Security Scan Commands
<command>

Important Directories
Frontend:

<path>

Backend:

<path>

Tests:

<path>

Documentation:

<path>

Additional Project Rules
Add repository-specific rules below:

<rule>
<rule>
<rule>
