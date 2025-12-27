---
name: prompt-optimizer
description: Optimizes prompts through an iterative Claude-GPT review process. Use when the user wants to optimize, improve, or refine a prompt.
---

# Prompt Optimization Skill

This skill guides an iterative prompt optimization process using both Claude and GPT as reviewers.

## Process Overview

### Step 1: Get Initial Prompt
Ask the user for the prompt they want to optimize. Clarify:
- What is the prompt's purpose?
- Who/what will receive this prompt?
- What's the desired output?

### Step 2: Optimize the Prompt
Improve the initial prompt by:
- Adding clarity and specificity
- Structuring with clear sections if needed
- Removing ambiguity
- Adding constraints or guardrails
- Improving instruction flow

Present the optimized version to the user with a brief explanation of changes.

### Step 3: GPT Review (Manual Handoff)
Provide the user with text to paste into GPT/ChatGPT:

```
Please review the following original prompt and its optimized version.

**Original Prompt:**
[original prompt here]

**Optimized Prompt (by Claude):**
[optimized prompt here]

Please:
1. Review both for weaknesses, strengths, and completeness
2. Create a rubric suitable for evaluating this type of prompt
3. Score the optimized prompt against your rubric (percentage for each criterion)
4. For any criterion scoring below 85%, improve the prompt to meet that criterion
5. Explain:
   - The rubric and scoring mechanism
   - The prompt results (before and after your improvements)
```

Tell the user: "Please paste this into ChatGPT, then paste GPT's response back here."

### Step 4: Claude Critique
After receiving GPT's response, review:
- The rubric GPT created (is it comprehensive? fair? well-calibrated?)
- The improved prompt (are the improvements valid?)
- Suggest improvements to both rubric and prompt if they would have significant impact

Be specific about what "significant impact" means:
- Addresses a blind spot in the rubric
- Fixes a logical flaw or ambiguity
- Meaningfully improves clarity or effectiveness

### Step 5: Iteration Check
Ask the user: "Would you like to continue iterating? The current improvements are [minor/moderate/significant]."

If yes, repeat from Step 3 with the latest prompt version.
If no, present the final optimized prompt with a summary of all improvements made.

## Output Format

Always clearly label:
- **Current Version**: The prompt being reviewed
- **Proposed Changes**: What you're suggesting
- **Rationale**: Why each change matters

## Handoff Template

When handing off to GPT, always format the text in a code block so the user can easily copy it.
