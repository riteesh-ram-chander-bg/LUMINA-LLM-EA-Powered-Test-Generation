# LUMINA-LLM-EA-Powered-Test-Generation

## Problem Statement

Traditional test generation tools like DynaMOSA and Pynguin focus on code coverage but fail to detect actual bugs effectively. Large Language Models can generate readable tests but lack consistency and optimization capabilities. Current approaches optimize for coverage metrics that correlate poorly with real bug detection.

## Solution

A hybrid approach combining **Evolutionary Algorithms** with **Large Language Models** to generate high-quality, bug-detecting unit tests for Python programs by leveraging systematic EA exploration with LLM semantic understanding.

## Core Pipeline

### 1. Static Code Analysis \& Type Inference

- Parse Python source code using AST
- Infer parameter types for dynamic functions
- Extract method signatures and dependencies


### 2. Initial LLM-Based Test Generation

- Generate seed test suite using GPT-4/similar models
- Create semantically meaningful initial test cases


### 3. Evolutionary Optimization

- Apply Genetic Algorithm (DEAP framework) to evolve test cases
- **Key difference**: Optimize for **mutation score** instead of coverage
- Run 50-100 generations targeting bug detection capability


### 4. Conditional LLM Invocation

- **Stagnation Detection**: Monitor EA progress (5+ generations without improvement)
- **Smart LLM Trigger**: Only invoke expensive LLM when EA stagnates
- **Prompt Mutation**: Evolve prompts based on surviving mutant analysis


### 5. Targeted Test Enhancement

- Analyze surviving mutants to identify missed bug types
- Generate targeted prompts for specific bug categories
- Inject LLM-enhanced tests back into EA population


### 6. Final Validation

- Continue evolution until 100% mutation score achieved
- Syntax validation and compilation checks


## GitHub Integration

**Browser Extension**:

- "Generate Tests" button in GitHub PR/file view
- Backend API runs complete pipeline
- Results displayed directly in GitHub UI
- One-click integration to `/tests/` directory

**Deployment**: Serverless backend handling code analysis and test generation with seamless GitHub API integration.

## Evaluation Metrics

### Primary Metric

- **Mutation Score**: Percentage of artificial bugs detected (target: 90%+)


### Secondary Metrics

- **Coverage**: Line and branch coverage using coverage.py
- **Real Bug Detection**: Performance on Refactory dataset
- **Efficiency**: API cost reduction (60-80%) and generation time (<5 min/function)


## Key Novelty

1. **Conditional LLM Intelligence**: LLM invocation only during EA stagnation, reducing costs while maintaining effectiveness
2. **Prompt Evolution**: Systematic prompt mutation based on surviving mutant analysis - first approach to treat prompts as evolvable genetic operators
3. **Mutation Score Optimization**: Direct optimization for bug detection capability rather than coverage metrics
4. **Production-Ready Integration**: GitHub browser extension for immediate developer adoption

## Expected Outcomes

- **90%+ mutation scores** vs 65-70% from traditional tools
- **60-80% reduction** in LLM API calls
- **Practical deployment** within existing developer workflows
- **Research advancement** in hybrid AI-EA approaches for software testing


## Implementation

- **Framework**: DEAP for Genetic Algorithm implementation
- **LLM Integration**: GPT-4/similar models with conditional invocation
- **Mutation Testing**: MutPy for artificial bug generation
- **Target**: Python programs with focus on unit test generation
